<template>
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
</template>

<script>
export default {
	data() {
		return {
			filter: "all",
		};
	},
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

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
	&:hover {
		transition: color 0.4s ease-in-out;
		color: var(--todo-text);
	}
}
</style>
