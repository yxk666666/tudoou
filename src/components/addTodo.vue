<template>
  		<header class="header">
				<h1>todos</h1>
				<input class="new-todo" placeholder="What needs to be done?" autofocus @keyup.enter="addtodo" v-model="newtodo">
			</header>
</template>
<script>
export default {
	data() {
		return {
			newtodo : ''
		}
	},
  methods : {
		addtodo() {
			this.$emit('addTodo', this.newtodo)
			this.newtodo = ''
		}
	}
}
</script>
