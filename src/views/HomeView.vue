<template>
  <div>
    <TreeView :lazyAmount="3" :treeElements="tabs" />
  </div>
</template>

<script>
import TreeView from "@/components/TreeView.vue";

export default {
  name: "HomePage",
  components: {
    TreeView,
  },
  data: () => ({
    tabs: [
      {
        id: 1,
        title: "Admins",
        showItems: false,
        items: [
          {
            id: 1,
            title: "Admin1",
            showItems: false,
            items: [
              {
                id: 1,
                title: "Admin1",
                showItems: false,
                items: [
                  {
                    id: 1,
                    title: "Admin1",
                    showItems: false,
                    items: [],
                  },
                ],
              },
            ],
          },
        ],
      },
      {
        id: 2,
        title: "Actions",
        showItems: false,
        items: [
          {
            id: 1,
            title: "Action1",
            showItems: false,
            items: [],
          },
          {
            id: 2,
            title: "Action2",
            showItems: false,
            items: [],
          },
          {
            id: 3,
            title: "Action3",
            showItems: false,
            items: [],
          },
          {
            id: 4,
            title: "Action4",
            showItems: false,
            items: [],
          },
          {
            id: 5,
            title: "Action5",
            showItems: false,
            items: [],
          },
          {
            id: 6,
            title: "Action6",
            showItems: false,
            items: [],
          },
          {
            id: 7,
            title: "Action7",
            showItems: false,
            items: [],
          },
          {
            id: 8,
            title: "Action8",
            showItems: false,
            items: [],
          },
          {
            id: 9,
            title: "Action9",
            showItems: false,
            items: [],
          },
          {
            id: 10,
            title: "Action10",
            showItems: false,
            items: [],
          },
          {
            id: 11,
            title: "Action11",
            showItems: false,
            items: [],
          },
          {
            id: 12,
            title: "Action12",
            showItems: false,
            items: [],
          },
          {
            id: 13,
            title: "Action13",
            showItems: false,
            items: [],
          },
          {
            id: 14,
            title: "Action14",
            showItems: false,
            items: [],
          },
          {
            id: 15,
            title: "Action15",
            showItems: false,
            items: [],
          },
          {
            id: 16,
            title: "Action16",
            showItems: false,
            items: [],
          },
          {
            id: 17,
            title: "Action17",
            showItems: false,
            items: [],
          },
          {
            id: 18,
            title: "Action18",
            showItems: false,
            items: [],
          },
          {
            id: 19,
            title: "Action19",
            showItems: false,
            items: [],
          },
          {
            id: 20,
            title: "Action20",
            showItems: false,
            items: [],
          },
          {
            id: 21,
            title: "Action21",
            showItems: false,
            items: [],
          },
        ],
      },
      {
        id: 3,
        title: "Group3",
        showItems: false,
        items: [],
      },
      {
        id: 4,
        title: "Group4",
        showItems: false,
        items: [],
      },
      {
        id: 5,
        title: "Group5",
        showItems: false,
        items: [],
      },
      {
        id: 6,
        title: "Group6",
        showItems: false,
        items: [],
      },
      {
        id: 7,
        title: "Group7",
        showItems: false,
        items: [],
      },
      {
        id: 8,
        title: "Group8",
        showItems: false,
        items: [],
      },
      {
        id: 9,
        title: "Group9",
        showItems: false,
        items: [],
      },
      {
        id: 10,
        title: "Group10",
        showItems: false,
        items: [],
      },
      {
        id: 11,
        title: "Group11",
        showItems: false,
        items: [],
      },
      {
        id: 12,
        title: "Group12",
        showItems: false,
        items: [],
      },
      {
        id: 13,
        title: "Group13",
        showItems: false,
        items: [],
      },
      {
        id: 14,
        title: "Group14",
        showItems: false,
        items: [],
      },
      {
        id: 15,
        title: "Group15",
        showItems: false,
        items: [],
      },
      {
        id: 16,
        title: "Group16",
        showItems: false,
        items: [],
      },
      {
        id: 17,
        title: "Group17",
        showItems: false,
        items: [],
      },
      {
        id: 18,
        title: "Group18",
        showItems: false,
        items: [],
      },
    ],
  }),
};
</script>
