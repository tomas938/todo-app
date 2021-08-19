<template>
	<router-view />
</template>

<style lang="scss">
@import "/src/scss/_variables";
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
html {
	font-size: 62.5%;
}
body {
	font-size: 1.8rem;
	font-family: $font-primary;
	background-color: red;
}
</style>
