<template>
	<Header @create-todo="newTodo($event)" />
	<main>
		<div class="wrapper">
			<VueDraggableNext class="todos" tag="ul">
				<transition-group name="list" appear>
					<li
						v-for="(todo, index) in filteredTodos"
						:key="todo.name"
						class="todo-item"
					>
						<div
							class="todo "
							:class="{ complete: todo.completed }"
							@click="todo.completed = !todo.completed"
						></div>
						<span :class="{ completed: todo.completed }">{{ todo.name }}</span>
						<svg
							@click="removeTodo(index)"
							class="close"
							xmlns="http://www.w3.org/2000/svg"
							width="18"
							height="18"
						>
							<path
								fill="#494C6B"
								fill-rule="evenodd"
								d="M16.97 0l.708.707L9.546 8.84l8.132 8.132-.707.707-8.132-8.132-8.132 8.132L0 16.97l8.132-8.132L0 .707.707 0 8.84 8.132 16.971 0z"
							/>
						</svg>
					</li>
				</transition-group>
			</VueDraggableNext>
			<div class="filters">
				<div class="items-left">
					<span>{{ filteredTodos.length }} items left</span>
				</div>
				<div class="filter">
					<span :class="{ active: filter === 'all' }" @click="filter = 'all'"
						>All</span
					>
					<span
						:class="{ active: filter === 'active' }"
						@click="filter = 'active'"
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
		</div>
	</main>
	<div class="filters-mobile">
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
	</div>
	<h3>Drag and drop to reorder items</h3>
</template>

<script>
import Header from "../components/Header";
import { VueDraggableNext } from "vue-draggable-next";
export default {
	components: {
		Header,
		VueDraggableNext,
	},
	data() {
		return {
			LOCAL_STORAGE_KEY: "todoApp",
			todos: JSON.parse(localStorage.getItem(this.LOCAL_STORAGE_KEY)) || [],
			filter: "all",
		};
	},
	mounted() {
		if (localStorage.getItem(this.LOCAL_STORAGE_KEY))
			this.todos = JSON.parse(localStorage.getItem(this.LOCAL_STORAGE_KEY));
	},
	watch: {
		todos: {
			deep: true,
			handler(newValue) {
				localStorage.setItem(this.LOCAL_STORAGE_KEY, JSON.stringify(newValue));
			},
		},
	},
	methods: {
		newTodo(newTodo) {
			if (newTodo !== "") {
				this.todos.unshift({
					name: newTodo,
					completed: false,
				});
			}
		},
		removeTodo(index) {
			this.todos.splice(index, 1);
		},
		clearTodos() {
			this.todos = this.todos.filter((todo) => !todo.completed);
		},
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

<style lang="scss" scoped>
@import "/src/scss/_variables";

main {
	transform: translateY(-3rem);
	display: flex;
	flex-direction: column;
	max-width: 73.5rem;
	margin: 0 auto;
	padding: 0 3rem;
}
.wrapper {
	box-shadow: 0px 0px 11px 0px #1a1919;
}
.todos {
	position: relative;
	border-radius: 0.5rem;
	background-color: var(--items-bg-color);
}
.todo-item {
	position: relative;
	display: flex;
	justify-content: space-between;
	align-items: center;
	width: 100%;
	padding: 2rem;
	padding-left: 8rem;
	font-family: $font-primary;
	font-weight: $light;
	color: var(--todo-text);
	border-bottom: 1px solid var(--todo-border);
	.todo {
		cursor: pointer;
		content: "";
		position: absolute;
		display: flex;
		align-items: center;
		justify-content: center;
		top: 50%;
		transform: translateY(-50%);
		left: 2.5rem;
		width: 3rem;
		height: 3rem;
		gap: 1rem;
		border-radius: 50%;
		border: 1px solid var(--todo-border);
		&:hover {
			border: 1px solid rgb(33, 21, 150);
		}
	}
	span {
		overflow: hidden;
		max-width: 95%;
		position: relative;
		&::before {
			opacity: 0;
			content: "";
			position: absolute;
			top: 50%;
			transform: translateY(-50%);
			left: 0;
			width: 10%;
			height: 0.2rem;
			background-color: $dark-grayish-blue--dark;
			transition: all 0.4s ease-in-out;
		}
		@media only screen and (max-width: 500px) {
			font-size: 1.4rem;
			width: 85%;
		}
	}
	.completed {
		color: $dark-grayish-blue--dark;
		position: relative;
		&::before {
			transition: all 0.4s ease-in-out;
			width: 100%;
			opacity: 1;
		}
	}
	.complete {
		background-image: url("../assets/icon-check.svg"), $primary-bg;
		background-repeat: no-repeat;
		background-position: center;
	}
	.close {
		cursor: pointer;
		opacity: 0;
	}
	&:hover {
		.close {
			transition: opacity 0.5s ease-in-out;
			opacity: 1;
		}
	}
}
.filters-mobile {
	display: none;
	background-color: var(--items-bg-color);
	padding: 2rem;
	box-shadow: 0px 0px 11px 0px #1a1919;
	border-radius: 0.5rem;
	margin: 0 3rem;
	@media only screen and (max-width: 600px) {
		display: block;
	}
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
}
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
	}
}
h3 {
	margin: 6rem 0;
	text-align: center;
	color: $dark-grayish-blue--dark;
	font-size: 1.8rem;
	@media only screen and (max-width: 600px) {
		font-size: 1.4rem;
	}
}
// TRANSITIONS //
.list-enter-active {
	transition: all 0.7s ease;
}
.list-enter-from {
	opacity: 0;
	transform: scale(0.6);
}
.list-enter-to {
	opacity: 1;
	transform: scale(1);
}
.list-leave-active {
	transition: all 0.7s ease;
	position: absolute;
}
.list-leave-from {
	opacity: 1;
	transform: scale(1);
}
.list-leave-to {
	opacity: 0;
	transform: scale(0.6);
}
.list-move {
	transition: all 0.4s ease;
}
</style>
