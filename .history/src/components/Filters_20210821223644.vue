<template>
	<div class="filters">
		<div class="items-left">
			<span>{{ todosLength }} items left</span>
		</div>
		<div class="filter">
			<span :class="{ active: filter === 'all' }" @click="filter = 'all'"
				>All</span
			>
			<span :class="{ active: filter === 'active' }" @click="filter = 'active'"
				>Active</span
			>
			<span
				:class="{ active: filter === 'completed' }"
				@click="filter = 'completed'"
				>Completed</span
			>
		</div>
		<div class="clear">
			<span @click="clearTodos">Clear Completed</span>
		</div>
	</div>
</template>

<script>
export default {
	props: ["todosLength", "todoData"],
	data() {
		return {
			filter: "all",
			todoData: null,
		};
	},
	computed: {
		filteredTodos() {
			if (this.filter === "all") {
				return this.todoData;
			} else if (this.filter === "active") {
				return this.todoData.filter((todo) => !todo.completed);
			} else if (this.filter === "completed") {
				return this.todoData.filter((todo) => todo.completed);
			}
			return this.todoData;
		},
	},
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

.filters {
	display: flex;
	justify-content: space-between;
	background-color: var(--items-bg-color);
	padding: 2rem;
	border-radius: 0.5rem;
	.filter {
		font-weight: $bold;
		display: flex;
		gap: 2rem;
		@media only screen and (max-width: 600px) {
			display: none;
		}
		.active {
			color: $primary;
			transition: color 0.3s ease-in-out;
		}
	}
	.items-left {
		span {
			cursor: auto;
		}
	}
	span {
		color: $dark-grayish-blue--dark;
		cursor: pointer;
		font-size: 1.7rem;
		@media only screen and (max-width: 350px) {
			font-size: 1.4rem;
		}
		&:hover {
			transition: color 0.4s ease-in-out;
			color: var(--todo-text);
		}
	}
}
</style>
