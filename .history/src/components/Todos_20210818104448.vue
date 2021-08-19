<template>
	<main>
		<ul class="todos">
			<li class="todo-item">
				<span>Learn Vue.js</span>
			</li>
			<li class="todo-item">
				<span>Learn Vue.js</span>
			</li>
		</ul>
	</main>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
main {
	display: flex;
	justify-content: center;
}
.todos {
	max-width: 67.5rem;
	width: 100%;
}
.todo-item {
	width: 100%;
	outline: none;
	border: none;
	padding: 2rem;
	padding-left: 8rem;
	border-radius: 0.5rem;
	font-size: 2rem;
	font-family: $font-primary;
	font-weight: $light;
	&::before {
		content: "";
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		left: 2.5rem;
		width: 3rem;
		height: 3rem;
		border-radius: 50%;
		border: 1px solid black;
	}
}
li {
	list-style: none;
}
</style>
