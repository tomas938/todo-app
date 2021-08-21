<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
</template>

<script>
export default {
	data() {
		return {
			filter: "all",
		};
	},
	computed: {
		filteredTodos() {
			if (this.filter === "all") {
				return this.todos;
			} else if (this.filter === "active") {
				return this.todos.filter((todo) => !todo.completed);
			} else if (this.filter === "completed") {
				return this.todos.filter((todo) => todo.completed);
			}
			return this.todos;
		},
	},
};
</script>

<style lang="scss" scoped></style>
