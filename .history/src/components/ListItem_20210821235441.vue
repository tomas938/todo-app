<template>
	<li class="todo-item">
		<div
			class="todo"
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
</template>

<script>
export default {};
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
		width: 4rem;
		height: 4rem;
		gap: 1rem;
		border-radius: 50%;
		border: 1px solid var(--todo-border);
		&:hover {
			border-top: 1px solid rgb(78, 194, 223);
			border-left: 1px solid rgb(78, 194, 223);
			border-right: 1px solid hsl(280, 87%, 65%);
			border-bottom: 1px solid hsl(280, 87%, 65%);
		}
	}
	span {
		overflow: hidden;
		max-width: 95%;
		position: relative;
		transition: all 0.4s ease-in-out;
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
	position: relative;
	z-index: 10;
	background-color: var(--items-bg-color);
	padding: 2rem;
	box-shadow: 0px 0px 11px 0px #1a1919;
	border-radius: 0.5rem;
	margin: 0 3rem;
	transition: all 0.4s ease-in-out;
	@media only screen and (max-width: 600px) {
		display: block;
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
		&:hover {
			transition: color 0.4s ease-in-out;
			color: var(--todo-text);
		}
	}
}
h3 {
	margin: 6rem 0;
	text-align: center;
	color: $dark-grayish-blue--dark;
	font-size: 1.8rem;
	position: relative;
	z-index: 10;
	@media only screen and (max-width: 600px) {
		font-size: 1.4rem;
	}
}
// TOGGLE TRANSITIONS //
.todos,
.filters,
.todo-item {
	transition: all 0.4s ease-in-out;
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
</style>
