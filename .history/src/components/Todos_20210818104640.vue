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
@import "/src/scss/_variables";

main {
	display: flex;
	justify-content: center;
}
.todos {
	max-width: 67.5rem;
	width: 100%;
}
.todo-item {
	position: relative;
	width: 100%;
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
	&::after {
		content: "";
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		right: 2.5rem;
		width: 3rem;
		height: 3rem;
		background-image: url(../assets/icon-croos.svg);
	}
}
li {
	list-style: none;
}
</style>
