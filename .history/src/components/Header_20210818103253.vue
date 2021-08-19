<template>
	<header>
		<nav class="nav container">
			<div class="nav__title">
				<h1>todo</h1>
			</div>
			<svg
				class="nav__theme"
				xmlns="http://www.w3.org/2000/svg"
				width="26"
				height="26"
			>
				<path
					fill="#FFF"
					fill-rule="evenodd"
					d="M13 0c.81 0 1.603.074 2.373.216C10.593 1.199 7 5.43 7 10.5 7 16.299 11.701 21 17.5 21c2.996 0 5.7-1.255 7.613-3.268C23.22 22.572 18.51 26 13 26 5.82 26 0 20.18 0 13S5.82 0 13 0z"
				/>
			</svg>
		</nav>
		<div class="new-todo">
			<input type="text" placeholder="Create a new todo..." />
		</div>
	</header>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

header {
	height: 30rem;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	gap: 5rem;
	padding: 1rem;
	background-image: url(../assets/bg-desktop-light.jpg);
	background-repeat: no-repeat;
	background-size: cover;
}
.nav {
	max-width: 67.5rem;
	width: 100%;
	display: flex;
	justify-content: space-between;
	align-items: baseline;
	&__title h1 {
		font-size: 4.5rem;
		letter-spacing: 1.8rem;
		text-transform: uppercase;
	}

	svg {
		cursor: pointer;
	}
}
.new-todo {
	max-width: 67.5rem;
	width: 100%;
	position: relative;
	&::before {
		content: "";
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		left: 2rem;
		width: 3rem;
		height: 3rem;
		border-radius: 50%;
		border: 1px solid black;
	}
}
input {
	width: 100%;
	outline: none;
	border: none;
	padding: 2rem;
	border-radius: 0.5rem;
	font-size: 2rem;
	font-family: $font-primary;
	font-weight: $light;
}
</style>
