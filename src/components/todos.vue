<template>
  <section class="main">
    <input id="toggle-all" class="toggle-all" type="checkbox">
    <label for="toggle-all">Mark all as complete</label>
    <ul class="todo-list">

      <!-- These are here just to show the structure of the list items -->
      <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
      <li
        v-for="item in filtertodo"
        :key="item.id"
        :class="{completed : item.isCompleted,editing : currentEdit === item.id}"
        @dblclick="editTodo(item.id)"
      >
        <div class="view">
          <input class="toggle" type="checkbox" v-model="item.isCompleted">
          <label>{{item.todo}}</label>
          <button class="destroy" @click="deltodo(item.id)"></button>
        </div>
        <input class="edit" v-model="item.todo" @keyup.enter="currentEdit= -1">
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  props: ["todoList"],
  data() {
    return {
      currentEdit: -1
    };
  },
  methods: {
    deltodo(id) {
      this.$emit("del", id);
    },
    editTodo(id) {
      this.currentEdit = id;
    }
  },
  computed :{
    filtertodo() {
    switch(this.$route.path){
      case '/' : 
      return  this.todoList
      case '/active' : 
      return this.todoList.filter(v=> !v.isCompleted)
      case '/completed' :
      return this.todoList.filter(v => v.isCompleted)
    }
    }
  }
};
</script>

