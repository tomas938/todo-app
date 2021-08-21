<template>
	<li v-for="(todo, index) in filteredTodos" :key="todo.name" class="todo-item">
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
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
