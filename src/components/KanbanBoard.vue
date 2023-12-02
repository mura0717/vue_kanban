<template>
  <div class="kanban-board">
    <div class="page-header">
      <h1>{{ msg }}</h1>
    </div>
    <div class="columns">
      <div class="column">
        <h3>To Do</h3>
        <div role="group">
          <input v-model="toDoTitle" class="input-area" placeholder="Title" />
          <br />
          <input
            v-model="toDoDescription"
            class="input-area"
            placeholder="Description"
          />
          <br />
          <button class="add-button" @click="addToDo()">Add New Item</button>
        </div>
        <template v-if="toDoBoard.length === 0">
          <p>No items in the 'To Do' list.</p>
        </template>
        <draggable
          v-model="toDoBoard"
          class="drag-area"
          :animation="300"
          :itemKey="id"
          group="tasks"
        >
          <template #item="{ element: item, index }">
            <div class="list-group-item" :key="item.id">
              {{ item.title }} - {{ item.description }}
              <button class="remove-button" @click="removeToDo(index)">
                Delete
              </button>
            </div>
          </template>
        </draggable>
      </div>
      <div class="column">
        <h3>In Process</h3>
        <div role="group">
          <input v-model="doingTitle" class="input-area" placeholder="Title" />
          <br />
          <input
            v-model="doingDescription"
            class="input-area"
            placeholder="Description"
          />
          <br />
          <button class="add-button" @click="addDoing()">Add New Item</button>
        </div>
        <template v-if="doingBoard.length === 0">
          <p>No items in the 'In Process' list.</p>
        </template>
        <draggable
          v-model="doingBoard"
          class="drag-area"
          :animation="300"
          :itemKey="id"
          group="tasks"
        >
          <template #item="{ element: item, index }">
            <div class="list-group-item" :key="item.id">
              {{ item.title }} - {{ item.description }}
              <button class="remove-button" @click="removeDoing(index)">
                Delete
              </button>
            </div>
          </template>
        </draggable>
      </div>
      <div class="column">
        <h3>Done</h3>
        <div role="group">
          <input v-model="doneTitle" class="input-area" placeholder="Title" />
          <br />
          <input
            v-model="doneDescription"
            class="input-area"
            placeholder="Description"
          />
          <br />
          <button class="add-button" @click="addDone()">Add New Item</button>
        </div>
        <template v-if="doneBoard.length === 0">
          <p>No items in the 'Done' list.</p>
        </template>
        <draggable
          v-model="doneBoard"
          class="drag-area"
          :animation="300"
          :itemKey="id"
          group="tasks"
        >
          <template #item="{ element: item, index }">
            <div class="list-group-item" :key="item.id">
              {{ item.title }} - {{ item.description }}
              <button class="remove-button" @click="removeDone(index)">
                Delete
              </button>
            </div>
          </template>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "KanbanBoard",
  props: {
    msg: String,
  },
  components: {
    draggable,
  },
  data() {
    return {
      toDoBoard: [],
      doingBoard: [],
      doneBoard: [],
      toDoTitle: "",
      toDoDescription: "",
      doingTitle: "",
      doingDescription: "",
      doneTitle: "",
      doneDescription: "",
      id: 0,
    };
  },
  methods: {
    generateNewItem: function (titleInput, descriptionInput) {
      const newItemId = String(++this.id);
      const newItemTitle = titleInput;
      const newItemDescription = descriptionInput;

      return {
        id: newItemId,
        title: newItemTitle,
        description: newItemDescription,
      };
    },
    addToDo: function () {
      if (this.toDoTitle && this.toDoDescription) {
        const newItem = this.generateNewItem(
          this.toDoTitle,
          this.toDoDescription
        );
        this.toDoBoard.push(newItem);
        this.toDoTitle = "";
        this.toDoDescription = "";
      } else {
        alert("Please enter both title and description");
      }
    },
    removeToDo: function (index) {
      console.log("remove item button clicked.");
      this.toDoBoard.splice(index, 1);
    },
    addDoing: function () {
      if (this.doingTitle && this.doingDescription) {
        const newItem = this.generateNewItem(
          this.doingTitle,
          this.doingDescription
        );
        this.doingBoard.push(newItem);
        this.doingTitle = "";
        this.doingDescription = "";
      } else {
        alert("Please enter both title and description");
      }
    },
    removeDoing: function (index) {
      this.doingBoard.splice(index, 1);
    },
    addDone: function () {
      if (this.doneTitle && this.doneDescription) {
        const newItem = this.generateNewItem(
          this.doneTitle,
          this.doneDescription
        );
        this.doneBoard.push(newItem);
        this.doneTitle = "";
        this.doneDescription = "";
      } else {
        alert("Please enter both title and description");
      }
    },
    removeDone: function (index) {
      this.doneBoard.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page-header {
  font-family: monospace;
}
.columns {
  display: flex;
}
.column {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
  padding: 10px; /* Adjust spacing as needed */
  border: 5px solid #000000; /* Optional border */
  margin: 0 20px; /* Adjust spacing as needed */
  background-color: blanchedalmond;
}

h3 {
  margin: 5px;
  padding-bottom: 10px;
  font-style: italic;
  font-weight: 900;
}

.drag-area {
  min-height: 150px; /* Set a minimum height */
  width: 95%; /* Ensure it spans the full width of the column */
  background-color: #f0f0f0; /* Optional: different background for visibility */
  border: 1px dashed #ccc;
}

.list-group-item {
  margin: 10px;
  padding: 5px;
  background-color: aqua;
  border: 1px solid #000000;
}

.input-area {
  margin: 2px;
}

.add-button {
  margin: 10px;
  background-color: greenyellow;
}

.remove-button {
  background-color: rgb(255, 0, 0);
}
</style>
