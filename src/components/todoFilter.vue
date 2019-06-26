<template>
  <footer class="footer">
    <!-- This should be `0 items left` by default -->
    <span class="todo-count">
      <strong>{{leftCount}}</strong> item left
    </span>
    <!-- Remove this if you don't implement routing -->
    <ul class="filters">
      <li>
        <a href="#/">All</a>
      </li>
      <li>
        <a href="#/active" >Active</a>
      </li>
      <li>
        <a href="#/completed">Completed</a>
      </li>
    </ul>
    <!-- Hidden if no completed items are left ↓ -->
    <button class="clear-completed" v-show="isShowbtn" @click ='clearCompleted'>Clear completed</button>
  </footer>
</template>
<script>
export default {
	props: ['todoList'],
	computed : {
	leftCount() {	
		return this.todoList.filter(v => !v.isCompleted).length
	},
	isShowbtn() {
		return this.todoList.some(v=> v.isCompleted)
	},
 
	},
   methods : {
  clearCompleted() {
    this.$emit('clearCompleted')
  }
  }

};
</script>

