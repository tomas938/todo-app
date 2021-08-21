<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
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

<style lang="scss" scoped></style>
