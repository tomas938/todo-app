<template>
	<router-view />
</template>

<style lang="scss">
@import "/src/scss/_variables";
:root {
	.dark {
		--items-bg-color: red;
	}
	.light {
		--items-bg-color: hsl(0, 0%, 100%);
		--body-bg: hsl(0, 0%, 98%);
	}
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
.light {
	background-color: var(--body-bg);
}

li {
	list-style: none;
}
</style>
