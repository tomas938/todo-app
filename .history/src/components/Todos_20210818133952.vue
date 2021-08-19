<template>
	<main>
		<ul class="todos">
			<li v-for="(todo,index) id todos" :key="index"></li>
			<!-- <li class="todo-item">
				<span>Learn Vue.js</span>
			</li>
			<li class="todo-item">
				<span>10 minutes meditation</span>
			</li> -->
			<div class="filters">
				<div class="items-left">
					<span>5 items left</span>
				</div>
				<div class="filter">
					<span>All</span>
					<span>Active</span>
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
		};
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
	width: 100%;
	padding: 2rem;
	padding-left: 8rem;
	font-size: 2rem;
	font-family: $font-primary;
	font-weight: $light;
	color: var(--todo-text);
	border-bottom: 1px solid var(--todo-border);

	// FIXME maybe group styling //
	&::before {
		cursor: pointer;
		content: "";
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		left: 2.5rem;
		width: 3rem;
		height: 3rem;
		border-radius: 50%;
		border: 1px solid var(--todo-border);
	}
	&::after {
		opacity: 0;
		cursor: pointer;
		content: "";
		position: absolute;
		right: 2.5rem;
		width: 2.6rem;
		height: 2.6rem;
		background-image: url(../assets/icon-cross.svg);
		background-repeat: no-repeat;
	}
	&:hover:after {
		transition: opacity 0.5s ease-in-out;
		opacity: 1;
	}
}
.filters {
	display: flex;
	justify-content: space-between;
	padding: 2rem;
	.filter {
		display: flex;
		gap: 2rem;
		span {
			font-weight: $bold;
			&:first-child {
				color: $primary;
			}
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
