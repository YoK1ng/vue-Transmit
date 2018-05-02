<template>
	<div id="app">
		<h1>组件通信</h1>
		<father></father>
	</div>
</template>

<script>
	import father from "@/components/father"

	export default {
		name: 'App',
		components: {
			father
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}

	div:not(#app) {
		margin: 30px;
		padding: 20px;
		color: #fff;
		border-radius: 10px;
	}

	h4{
		color: #000;
	}
	h5{
		color: #222;
	}
	button{
		padding: 5px 10px;
	}
</style>