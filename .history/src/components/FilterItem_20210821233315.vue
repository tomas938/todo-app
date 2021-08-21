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
	props: ["todos"],
	data() {
		return {
			filter: "all",
		};
	},
	computed: {
		filteredTodos() {
			if (this.filter === "active") {
				console.log("hex");
				return this.todos.filter((todo) => !todo.completed);
			} else if (this.filter === "completed") {
				return this.todos.filter((todo) => todo.completed);
			}
			return this.todos;
		},
	},
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

.filter {
	font-weight: $bold;
	display: flex;
	justify-content: center;
	gap: 2rem;
	.active {
		color: $primary;
		transition: color 0.3s ease-in-out;
	}
}
span {
	color: $dark-grayish-blue--dark;
	cursor: pointer;
	font-size: 1.7rem;
	@media only screen and (max-width: 350px) {
		font-size: 1.4rem;
	}
}
</style>
