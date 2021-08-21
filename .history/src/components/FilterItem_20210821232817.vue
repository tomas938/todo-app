<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">All</span>
	<span :class="{ active: filter === 'active' }" @click="filter = 'active'"
		>Active</span
	>
	<span
		:class="{ active: filter === 'completed' }"
		@click="filter = 'completed'"
		>Completed</span
	>
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
			if (this.filter === "active") {
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
