<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
