<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
</template>

<script>
export default {
	props: ["todos"],
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
			console.log(this.todos);
		},
	},
};
</script>

<style lang="scss" scoped></style>
