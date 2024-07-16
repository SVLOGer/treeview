<template>
  <div class="root elementsContainer">
    <div class="d-flex" @click="switchShowItems()">
      <v-list-item-title>{{ treeElement.title }}</v-list-item-title>
      <v-list-item-icon v-if="treeElement.items.length > 0">
        <v-icon v-if="!showItems"> mdi-menu-left </v-icon>
        <v-icon v-else> mdi-menu-down </v-icon>
      </v-list-item-icon>
    </div>
    <div v-if="showItems" id="treeElements" ref="treeElements">
      <v-list-item
        v-for="(item, index) in visibleTreeElements"
        :key="item.id"
        class="pr-0"
        :ref="index === visibleTreeElements.length - 1 ? 'lastVisibleEl' : null"
      >
        <TreeElement :treeElement="item" :lazyAmount="lazyAmount" />
      </v-list-item>
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeElement",
  props: {
    treeElement: {
      type: Object,
      required: true,
    },
    lazyAmount: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      showItems: this.treeElement.showItems || false,
      visibleCount: this.lazyAmount,
      lastVisibleElObserver: null,
    };
  },
  computed: {
    visibleTreeElements() {
      return this.treeElement.items.slice(0, this.visibleCount);
    },
    maxVisibleElements() {
      return this.treeElement.items.length;
    },
  },
  methods: {
    switchShowItems() {
      if (this.treeElement.items.length > 0) {
        this.showItems = !this.showItems;
        if (this.showItems) {
          this.$nextTick(() => {
            this.observeLastVisibleElement();
          });
        } else {
          this.disconnectObserver();
        }
      }
    },
    observeLastVisibleElement() {
      this.$nextTick(() => {
        const lastVisibleEl = this.$el.querySelector(
          "#treeElements > .v-list-item:last-child"
        );
        if (lastVisibleEl && this.visibleCount < this.maxVisibleElements) {
          this.lastVisibleElObserver = new IntersectionObserver(
            (entries) => {
              entries.forEach((entry) => {
                if (entry.isIntersecting) {
                  if (
                    lastVisibleEl.getBoundingClientRect().top +
                      lastVisibleEl.getBoundingClientRect().height <=
                    400
                  ) {
                    this.visibleCount += this.lazyAmount;
                  }
                  this.lastVisibleElObserver.unobserve(entry.target);
                  if (this.visibleCount < this.maxVisibleElements) {
                    this.$nextTick(() => {
                      this.observeLastVisibleElement();
                    });
                  }
                }
              });
            },
            {
              root: this.$el.querySelector("#treeElements"),
              rootMargin: "0px",
              threshold: 1.0,
            }
          );
          this.lastVisibleElObserver.observe(lastVisibleEl);
        }
      });
    },
    disconnectObserver() {
      if (this.lastVisibleElObserver) {
        this.lastVisibleElObserver.disconnect();
        this.lastVisibleElObserver = null;
      }
    },
  },
};
</script>

<style>
.elementsContainer {
  width: 100%;
}
</style>
