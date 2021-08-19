<template>
	<main>
		<ul class="todos">
			<li v-for="(todo, index) in todos" :key="index" class="todo-item">
				<div class="todo" @click="changeStatus()" :class="{ complete }">
					<svg xmlns="http://www.w3.org/2000/svg" width="11" height="9">
						<path
							fill="none"
							stroke="#FFF"
							stroke-width="2"
							d="M1 4.304L3.696 7l6-6"
						/>
					</svg>
				</div>
				<!-- <div class="todo-empty" v-else></div> -->
				<span>{{ todo }}</span>
				<svg
					@click="removeTodo()"
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
			<div class="filters">
				<div class="items-left">
					<span>{{ todos.length }} items left</span>
				</div>
				<div class="filter">
					<span :class="{ active }">All</span>
					<span :class="{ active: completed }">Active</span>
					<span>Completed</span>
				</div>
				<div class="clear">
					<span>Clear Completed</span>
				</div>
			</div>
		</ul>
	</main>
</template>

<script>
export default {
	data() {
		return {
			todos: [
				"Jog around the park 3x",
				"10 minutes meditation",
				"Read for 1 hour",
				"Pick up grocerie",
				"Complete Todo App on Frontend Mentor",
			],
			complete: true,
			active: true,
			completed: false,
			all: false,
		};
	},
	methods: {
		changeStatus() {
			this.complete = !this.complete;
		},
		removeTodo(index) {
			this.todos.splice(index, 1);
		},
	},
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

main {
	padding: 0 3rem;
	display: flex;
	justify-content: center;
	transform: translateY(-5rem);
}
.todos {
	max-width: 67.5rem;
	width: 100%;
	border-radius: 0.5rem;
	background-color: var(--items-bg-color);
	box-shadow: 0px 0px 11px 0px #1a1919;
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

	// FIXME maybe group styling //
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
		border-radius: 50%;
		border: 1px solid var(--todo-border);
	}
	.complete {
		background: $primary-bg;
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
.filters {
	display: flex;
	justify-content: space-between;
	padding: 2rem;
	.filter {
		display: flex;
		gap: 2rem;
		.active {
			font-weight: $bold;
			color: $primary;
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
	}
}
</style>
