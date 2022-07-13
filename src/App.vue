<template>
	<div id="app">
		<random-cat></random-cat>
	</div>
</template>

<script>
	import RandomCat from '@/components/RandomCat.vue';

	export default {
		name: 'App',
		components: {
			'random-cat': RandomCat,
		},
	};
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500&display=swap');
	@import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	#app {
		font-family: 'Montserrat', sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #31525b;
		height: 100vh;
		background: #fe91a8;
	}
</style>
