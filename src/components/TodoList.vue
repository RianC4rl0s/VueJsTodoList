<template>
  <div class="app app-text">
    <h1 class="title-1">TodoList</h1>
    <ol>
      <li v-for="(todo, index) in todos" :key="index">
        <p>
          {{ todo.text }}
          <button class="remove-btn" @click="deleteTableRow(index)">-</button>
        </p>
      </li>
    </ol>
    <div class="inputs">
      <form>
        <input class="text-field-1" placeholder="Todo" v-model="text" />
        <div class="buttons">
          <button type="sub" class="add-btn" @click="addTodo(text)">+</button>
          <button class="remove-btn" @click="removeTodos">Remove All</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    msg: String,
  },
  data() {
    return {
      todos: [{ id: 1, text: "Learn VueJs" }],
      text: "",
    };
  },
  methods: {
    addTodo(text) {
      if (text !== "") {
        this.todos.push({
          id: this.todos.lenghts + 1,
          text,
        });
        this.text = "";
      }
    },
    removeTodos() {
      this.todos = [];
    },
    deleteTableRow(idx) {
      //this.counter--;
      this.todos.splice(idx, 1);
    },
  },
};
</script>
<style>
/* body{
  background-color: rgb(35, 35, 35);
}
.app-text{
  color: rgb(235, 235, 235);
} */
.text-field-1 {
  width: 300px;
  height: 28px;
  border-radius: 12px;
  border: 1px solid rgb(174, 174, 174);
}
.text-field-1:focus  {
  border: 1px solid rgb(243, 4, 4);
}
.buttons button {
  height: 28px;
  margin: 5px;
  min-width: 28px;
  border-radius: 6px;
  border: 1px solid rgba(174, 174, 174, 0.027);
}
.remove-btn {
  background-color: rgb(204, 0, 0);
  height: 28px;
  margin: 5px;
  min-width: 28px;
  border-radius: 6px;
  border: 1px solid rgba(174, 174, 174, 0);
  font-weight: 700;
  color: azure;
  box-shadow: 1px 1px 5px rgb(193, 193, 193);
}
.remove-btn:hover {
  background-color: rgb(222, 3, 3);
}
.remove-btn:active {
  background-color: rgb(152, 0, 0);
}
.add-btn {
  background-color: rgb(72, 211, 109);
  height: 28px;
  margin: 5px;
  min-width: 28px;
  border-radius: 6px;
  border: 1px solid rgba(174, 174, 174, 0);
  font-weight: 700;
  color: azure;
  box-shadow: 1px 1px 5px rgb(193, 193, 193);
}
.add-btn:hover {
  background-color: rgb(80, 230, 120);
}
.add-btn:active {
  background-color: rgb(60, 184, 93);
}
</style>


