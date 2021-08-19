<template>
	<header>
		<nav class="nav container">
			<div class="nav__title">
				<h1>todo</h1>
			</div>
			<svg
				v-if="ligth"
				@click="changeTheme"
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
			<svg
				v-else
				@click="changeTheme"
				xmlns="http://www.w3.org/2000/svg"
				width="26"
				height="26"
			>
				<path
					fill="#FFF"
					fill-rule="evenodd"
					d="M13 21a1 1 0 011 1v3a1 1 0 11-2 0v-3a1 1 0 011-1zm-5.657-2.343a1 1 0 010 1.414l-2.121 2.121a1 1 0 01-1.414-1.414l2.12-2.121a1 1 0 011.415 0zm12.728 0l2.121 2.121a1 1 0 01-1.414 1.414l-2.121-2.12a1 1 0 011.414-1.415zM13 8a5 5 0 110 10 5 5 0 010-10zm12 4a1 1 0 110 2h-3a1 1 0 110-2h3zM4 12a1 1 0 110 2H1a1 1 0 110-2h3zm18.192-8.192a1 1 0 010 1.414l-2.12 2.121a1 1 0 01-1.415-1.414l2.121-2.121a1 1 0 011.414 0zm-16.97 0l2.121 2.12A1 1 0 015.93 7.344L3.808 5.222a1 1 0 011.414-1.414zM13 0a1 1 0 011 1v3a1 1 0 11-2 0V1a1 1 0 011-1z"
				/>
			</svg>
		</nav>
		<div class="new-todo">
			<input type="text" placeholder="Create a new todo..." />
		</div>
	</header>
</template>

<script>
export default {
	data() {
		return {
			ligth: true,
			body: document.body,
		};
	},
	methods: {
		changeTheme() {
			this.ligth = !this.ligth;
			if (this.ligth) {
				this.body.classList.remove("light");
				this.body.classList.add("dark");
			}

			// } else {
			// 	this.body.classList.add("light");
			// }
		},
	},
	mounted() {
		this.body.classList.add("light");
	},
};
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
	padding: 3rem;
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
		left: 2.5rem;
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
	padding-left: 8rem;
	border-radius: 0.5rem;
	font-size: 2rem;
	font-family: $font-primary;
	font-weight: $light;
}
</style>
