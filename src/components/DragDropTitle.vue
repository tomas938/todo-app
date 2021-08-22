<template>
	<h3>
		<slot></slot>
	</h3>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

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
</style>
