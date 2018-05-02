<template>
	<div>
		<h4>{{name}}</h4>
		<h5>下级:{{znamea}} {{znameb}}</h5>
		<button @click="bta">{{name}}触发{{znamea}}</button>
		<button @click="btb">{{name}}触发{{znameb}}</button>

		<sona :fname="name" @ztf="ztf" ref="ftza" @znamea="znameaf"></sona>
		<sonb :fname="name" @ztf="ztf" ref="ftzb" @znameb="znamebf"></sonb>

	</div>
</template>

<script>
	import sona from "@/components/sona"
	import sonb from "@/components/sonb"

	export default {
		name: 'App',
		components: {
			sona , sonb
		},
		data() {
			return {
				name: "父组件",
				znamea:"",
				znameb:"",
			}
		},
		methods: {
			ztf(){
				alert("我是"+this.name+"事件")
			},
			bta(){
				this.$refs.ftza.stz();
			},
			btb(){
				this.$refs.ftzb.stz();
			},
		    znameaf(data) {
		    	this.znamea = data;
		    },
		    znamebf(data) {
		    	this.znameb = data;
		    }
		}
	}
</script>

<style scoped="">
	div{
		background: #409EFF;
	}
</style>

<!--
	一：父传值子
	1、父组件通过“:”传值								:content="item"
	2、子组件通过“props”接受，页面调用{{content}}		props:['content']

	二：父传事件子
	1、挂载								ref="ftz"
	2、触发挂载组件方法					this.$refs.ftz.stz();

	三：子传值父
	1、子组件通过“$emit”传值				this.$emit("zdel", this.index)
	2、父组件接受事件					@zdel="触发事件"
	3、父组件mounted()处理				mounted(){ zdel(){} }

	四：子传事件父
	1、子组件创建事件传递					@click="del(index)"
	2、子组件通过“$emit”传值				this.$emit("zdel", this.index)
	3、父组件接受事件					@zdel="触发事件"

	五：同级传值
	新建bus.js
	import Vue from 'vue'
	export var bus = new Vue()
	1、引入								import {bus} from "@/bus.js"
	2、mounted传值						bus.$emit("tnamea",this.name)
	3、created接收						bus.$on("tnamea", data => (this.tname = data));

	六：同级传事件
	1、引入								import {bus} from "@/bus.js"
	2、触发事件							@click="bt"
	3、$emit传递事件						bus.$emit("tbta")
	4、created接收事件					bus.$on('tbta' ,function(){ }.bind(this));
-->