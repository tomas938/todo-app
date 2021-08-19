<template>
	<router-view />
</template>

<style lang="scss">
@import "/src/scss/_variables";
:root {
	--bg-color: $very-light-grayish-blue;
}
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
}
li {
	list-style: none;
}
</style>
