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
	computed: {
		filteredTodos() {
			if (this.filter === "all") {
				return this.todos;
			}
			return this.todos;
		},
	},
};
</script>

<style lang="scss" scoped></style>
