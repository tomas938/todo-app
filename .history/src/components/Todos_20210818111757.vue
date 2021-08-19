<template>
	<main>
		<ul class="todos">
			<li class="todo-item">
				<span>Learn Vue.js</span>
			</li>
			<li class="todo-item">
				<span>Learn Vue.js</span>
			</li>
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
export default {};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

main {
	display: flex;
	justify-content: center;
	transform: translateY(-5rem);
}
.todos {
	max-width: 67.5rem;
	width: 100%;
	border-radius: 0.5rem;
}
.todo-item {
	position: relative;
	width: 100%;
	padding: 2rem;
	padding-left: 8rem;
	font-size: 2rem;
	font-family: $font-primary;
	font-weight: $light;
	border: 1px solid black;

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
		border: 1px solid black;
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
	border: 1px solid black;
	padding: 2rem;
	.filter {
		display: flex;
		gap: 2rem;
	}
	.items-left {
		span {
			cursor: normal;
		}
	}
	span {
		cursor: pointer;
		font-size: 1.7rem;
	}
}
li {
	list-style: none;
}
</style>
