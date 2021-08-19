<template>
	<router-view />
</template>

<style lang="scss">
@import "/src/scss/_variables";
:root {
	.dark {
		--bg-image: url(./assets/bg-desktop-dark.jpg);
		--items-bg-color: hsl(235, 24%, 19%);
		--body-bg: hsl(235, 21%, 11%);
		--todo-text: hsl(236, 33%, 92%);
		--todo-border: hsl(237, 14%, 26%);
	}
	.light {
		--bg-image: url(./assets/bg-desktop-light.jpg);
		--items-bg-color: hsl(0, 0%, 100%);
		--body-bg: hsl(0, 0%, 98%);
		--todo-text: hsl(233, 14%, 35%);
		--todo-border: hsl(236, 33%, 92%);
	}
}
#app {
	display: flex;
	flex-direction: column;
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
	background-color: var(--body-bg);
}

li {
	list-style: none;
}
</style>
