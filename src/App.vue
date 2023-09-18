<template>
  <div class="dashboard-container">
    <div class="left-drawer">
      <div
        v-for="(item, index) in arr"
        :key="index"
        @click="noteSelected(item, index)"
        :class="{ cards: true, highlightedCard: selectedIndex === index }"
      >
        <div class="list-item-heading">
          <span>
            <p class="heading">
              <b>{{ item["id"] }}</b>
            </p>
          </span>
          <span>
            <button
              type="button"
              @click.stop="deleteItem(index)"
              class="delete"
            >
              delete
            </button>
          </span>
        </div>
        <p class="description">{{ item["description"] }}</p>
      </div>
    </div>
    <div class="right-drawer">
      <p v-if="isObjectEmpty()" class="empty">Please select any Note</p>
      <div v-else class="notes-display" @click="unselectNote()">
        <h1 class="head">{{ selectedNote["id"] }}</h1>
        <p>{{ selectedNote["description"] }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data: function () {
    return {
      arr: [
        {
          id: "this is a note book 1",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 2",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 3",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 4",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 5",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 6",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 7",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 8",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 9",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 10",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 11",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 12",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 14",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
        {
          id: "this is a note book 15",
          description:
            "  Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatibus sunt, odio, veniam vel nesciunt nisi mollitia numquam repellendus, distinctio quae nobis",
        },
      ],
      selectedNote: {},
      selectedIndex: -1,
    };
  },
  methods: {
    isObjectEmpty() {
      return Object.keys(this.selectedNote).length === 0;
    },
    noteSelected: function (item, index) {
      this.selectedNote = Object.assign({}, item);
      this.selectedIndex = index;
      console.log(this.selectedNote);
    },
    unselectNote: function () {
      this.selectedNote = {};
    },
    deleteItem: function (index) {
      this.arr.splice(index, 1);
      if (this.selectedIndex === index) {
        console.log("coming is");
        this.selectedNote = {};
        this.selectedIndex = -1;
      }
    },
  },
};
</script>
<style lang="scss">
body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.dashboard-container {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-areas: "left right right right";
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 100%;
  overflow: hidden;
}

.left-drawer {
  grid-area: left;
  height: 100vh;
  overflow-y: scroll;
  overflow-x: hidden;
}

.right-drawer {
  grid-area: right;
  height: 100%;
  display: flex;
  align-items: center;
}

.cards {
  cursor: pointer;
  margin: 10px;
  height: 100px;
  border: 2px solid black;
  white-space: nowrap;
  overflow: hidden;
}

.description {
  overflow: hidden;
  text-overflow: ellipsis;
  margin-left: 5px;
}

.heading {
  margin-left: 2px;
}

.head {
  border-bottom: 2px solid black;
}

.empty {
  flex: 1;
  text-align: center;
}

.notes-display {
  margin: 10px;
  height: 100%;
  width: 100%;
}

.highlightedCard {
  color: white;
  background-color: black;
}

.list-item-heading {
  padding-left: 1vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid black;
}

.delete {
  margin-right: 1vh;
}
</style>
