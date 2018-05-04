# 安装
npm install

# 启动服务 localhost:8080
npm run dev

# 打包
npm run build

## 语法

# 父传值子
1、父组件传值     :content="item"

2、子组件“props”接受     props:['content']

3、页面调用     {{content}}

# 父传事件子
1、挂载     ref="ftz"

2、触发挂载组件方法     this.$refs.ftz.stz();

# 子传值父
1、子组件通过“$emit”传值     this.$emit("zdel", this.index)

2、父组件接受事件     @zdel="触发事件"

3、父组件mounted()处理     mounted(){ zdel(){} }

# 子传事件父
1、子组件创建事件传递     @click="del(index)"

2、子组件通过“$emit”传值     this.$emit("zdel", this.index)

3、父组件接受事件     @zdel="触发事件"

# 同级传值
新建bus.js

import Vue from 'vue'

export var bus = new Vue()

1、引入     import {bus} from "@/bus.js"

2、mounted传值     bus.$emit("tnamea",this.name)

3、created接收     bus.$on("tnamea", data => (this.tname = data));

# 同级传事件
1、引入     import {bus} from "@/bus.js"

2、触发事件     @click="bt"

3、$emit传递事件     bus.$emit("tbta")

4、created接收事件     bus.$on('tbta' ,function(){ }.bind(this));
