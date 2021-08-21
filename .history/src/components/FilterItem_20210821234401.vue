<template>
	<span :class="{ active: filter === 'all' }" @click="filter = 'all'">
		<slot></slot>
	</span>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
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
}
</style>
