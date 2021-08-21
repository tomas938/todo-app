<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
</template>

<script>
export default {
	filter: "all",
};
</script>

<style lang="scss" scoped></style>
