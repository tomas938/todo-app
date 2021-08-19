<template>
	<Header @create-todo="log()" />
	<Todos />
</template>

<script>
import Header from "../components/Header";
import Todos from "../components/Todos.vue";
export default {
	components: {
		Header,
		Todos,
	},
};
</script>
<style lang="scss"></style>
