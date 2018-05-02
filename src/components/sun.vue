<template>
	<div class="app">
		<h4>我是{{name}}</h4>
		<h5>上级:{{fname}} {{zname}}</h5>
		<button @click="bt">{{name}}触发{{zname}}</button>
	</div>
</template>

<script>
	export default {
		name: "app",
		props:['fname','zname'],
		data() {
			return {
				name: "孙组件"
			}
		},
		methods:{
			bt(){
				this.$emit("stz")
			},
			stf(){
				alert("我是"+this.name+"事件")
			}
		},
		mounted(){
			this.$emit('sname',this.name)
		}
	}
</script>

<style scoped="">
	div.app{
		background: #E6A23C;
	}
</style>