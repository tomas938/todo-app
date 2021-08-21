<template>
	<li class="todo-item">
		<div
			class="todo"
			:class="{ complete: todo.completed }"
			@click="todo.completed = !todo.completed"
		></div>
		<span :class="{ completed: todo.completed }">{{ todo }}</span>
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
export default {
	props: ["todo"],
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";
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
</style>
