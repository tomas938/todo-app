<template>
	<!-- <span :class="{ active: filter === 'all' }" @click="filter = 'all'"
						>All</span
					> -->
	<span :class="{ active: filter === 'active' }" @click="filter = 'active'"
		>Active</span
	>
	<span
		:class="{ active: filter === 'completed' }"
		@click="filter = 'completed'"
		>Completed</span
	>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
