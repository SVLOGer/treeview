<template>
  <div>
    <v-card class="mx-auto" width="300">
      <div class="treeElements" @scroll="onScroll" ref="treeList">
        <v-list>
          <v-list-item
            v-for="treeElement in visibleTreeElements"
            :key="treeElement.id"
            class="pr-2"
          >
            <TreeElement :treeElement="treeElement" :lazyAmount="lazyAmount" />
          </v-list-item>
        </v-list>
      </div>
    </v-card>
  </div>
</template>

<script>
import TreeElement from "@/components/TreeElement.vue";

export default {
  name: "TreeView",
  components: {
    TreeElement,
  },
  props: {
    treeElements: {
      type: Array,
      required: true,
    },
    lazyAmount: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      visibleCount: this.lazyAmount,
      windowHeight: 0,
    };
  },
  computed: {
    visibleTreeElements() {
      return this.treeElements.slice(0, this.visibleCount);
    },
  },
  methods: {
    onScroll() {
      const treeList = this.$refs.treeList;
      if (
        treeList.scrollTop + treeList.clientHeight >=
        treeList.scrollHeight - 10
      ) {
        this.loadMore();
      }
    },
    loadMore() {
      if (this.visibleCount < this.treeElements.length) {
        this.visibleCount += this.lazyAmount;
        this.$nextTick(this.checkForScroll);
      }
    },
    checkForScroll() {
      const treeList = this.$refs.treeList;
      if (
        treeList.scrollHeight <= treeList.clientHeight &&
        this.visibleCount < this.treeElements.length
      ) {
        if (this.visibleCount < this.treeElements.length) {
          this.visibleCount += 1;
          this.$nextTick(this.checkForScroll);
        }
      }
    },
  },
  mounted() {
    this.$nextTick(this.checkForScroll);
  },
};
</script>

<style>
.treeElements {
  max-height: 400px; /* Установите максимальную высоту для включения прокрутки */
  overflow-y: auto;
}
</style>
