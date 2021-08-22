<template>
	<div class="filters">
		<div class="items-left">
			<span>{{ filteredTodos.length }} items left</span>
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
export default {};
</script>

<style lang="scss" scoped>
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

// TRANSITION GROUP //

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
