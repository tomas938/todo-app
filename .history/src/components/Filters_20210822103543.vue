<template>
	<div class="filters">
		<div class="items-left">
			<span>items left</span>
		</div>
		<div class="filter">
			<span
				:class="{ active: filter === 'all' }"
				@click="$emit('all'), (filter = 'all')"
				>All</span
			>
			<span
				:class="{ active: filter === 'active' }"
				@click="$emit('active'), (filter = 'active')"
				>Active</span
			>
			<span
				:class="{ active: filter === 'completed' }"
				@click="$emit('completed'), (filter = 'completed')"
				>Completed</span
			>
		</div>
		<div class="clear">
			<span @click="clearTodos">Clear Completed</span>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			filter: "all",
		};
	},
};
</script>

<style lang="scss" scoped>
@import "/src/scss/_variables";

.filters {
	display: flex;
	justify-content: space-between;
	background-color: var(--items-bg-color);
	padding: 2rem;
	border-radius: 0.5rem;
	.filter {
		font-weight: $bold;
		display: flex;
		gap: 2rem;
		@media only screen and (max-width: 600px) {
			display: none;
		}
		.active {
			color: $primary;
			transition: color 0.3s ease-in-out;
		}
	}
	.items-left {
		span {
			cursor: auto;
		}
	}
	span {
		color: $dark-grayish-blue--dark;
		cursor: pointer;
		font-size: 1.7rem;
		@media only screen and (max-width: 350px) {
			font-size: 1.4rem;
		}
		&:hover {
			transition: color 0.4s ease-in-out;
			color: var(--todo-text);
		}
	}
}

// TOGGLE TRANSITIONS //

.filters {
	transition: all 0.4s ease-in-out;
}
</style>
