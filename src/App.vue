<template>
  <div id="app">
    <section class="todoapp">
      <add-todo @addTodo="addTodo"></add-todo>
      <todos :todoList="todoList" @del="del"></todos>
      <todo-filter :todoList="todoList" @clearCompleted='clearCompleted'></todo-filter>
    </section>
    <footer class="info">
      <p>Double-click to edit a todo</p>
      <!-- Remove the below line ↓ -->
      <p>
        Template by
        <a href="http://sindresorhus.com">Sindre Sorhus</a>
      </p>
      <!-- Change this out with your name and url ↓ -->
      <p>
        Created by
        <a href="http://todomvc.com">you</a>
      </p>
      <p>
        Part of
        <a href="http://todomvc.com">TodoMVC</a>
      </p>
    </footer>
  </div>
</template>
<script>
import addTodo from "./components/addTodo";
import todos from "./components/todos";
import todoFilter from "./components/todoFilter";
export default {
  components: {
    addTodo,
    todos,
    todoFilter
  },
  data() {
    return {
      todoList: [
        {
          id: 2,
          todo: "买了伞，千万不能把伞淋湿了藏起来",
          isCompleted: false
        },
        {
          id: 3,
          todo: "不买伞了，太贵了",
          isCompleted: false
        }
      ]
    };
  },
  methods: {
    del(id) {
      this.todoList = this.todoList.filter(v => v.id != id);
    },
    addTodo(value) {
      // console.log(value)
      let newTodo = {
        id: this.todoList.length? this.todoList[this.todoList.length - 1].id + 1: 1,
        todo: value,
        isCompleted: false
      };
      this.todoList.push(newTodo);
    },
    clearCompleted() {
      this.todoList = this.todoList.filter(v => !v.isCompleted)
    }
  }
};
</script>



