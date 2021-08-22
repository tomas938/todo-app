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
export default {};
</script>

<style lang="scss" scoped>
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
</style>
