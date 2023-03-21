---
title: vue脚手架分析
author: 学绅
tags: Vue
categories: note
date: 2022-12-20 14:23:00
# 加入时间线
selected: true
---

vue脚手架文件结构分析

<!-- more -->

# vue脚手架分析

## 一. 初始化脚手架
### 1. 全局安装@vue/cli
```npm install -g @vue/cli```

注意，此前若安装过旧版本的vue，请清理干净后，再行安装。

tips: 可使用此指定检查vue是否安装成功 ``vue -V``
### 2. 切换到要创建项目的目录，使用命令创建项目
```vue create xxx```

### 3. 启动项目
```npm run serve```


## 二. 脚手架文件结构

	├── node_modules 
	├── public
	│   ├── favicon.ico: 页签图标
	│   └── index.html: 主页面
	├── src
	│   ├── assets: 存放静态资源
	│   │   └── logo.png
	│   │── component: 存放组件
	│   │   └── HelloWorld.vue
	│   │── App.vue: 汇总所有组件
	│   │── main.js: 入口文件
	├── .gitignore: git版本管制忽略的配置
	├── babel.config.js: babel的配置文件
	├── package.json: 应用包配置文件 
	├── README.md: 应用描述文件
	├── package-lock.json：包版本控制文件
    

    
## 三. 主要文件结构分析

### main.js
``` js
//main.js是整个项目的入口文件

// 此处引入的默认为vue.runtime.xxx.js（运行版的Vue，只包含核心功能，没有模板解析器）
import Vue from 'vue'  // 引入vue，
import App from './App.vue'  // 引入App组件，它是所有组件的父组件
Vue.config.productionTip = false  // 关闭Vue生产提示

// 创建Vue实例对象--vm
new Vue({
  el:'#app',
  // 因为vue.runtime.xxx.js没有模板解析器，所以不能使用template配置项，
  // 需要使用render函数接收到的createElement函数去指定具体内容。
  render:h => h(App)
})
```

### App.vue
``` vue
// App.vue，汇总所有组件，其余组件放置于 components文件夹中，结构与此类似

<template>
  <!-- 模板区域，因为模板只能有一个根，所以要用一个div或其他标签包裹 -->
  <div></div>
</template>

<script>
  // Vue、js区域，此处的代码需要暴露，main.js才能使用
  export default{
    name:'App'
  }
</script>

<style>
  /* 样式区域 */
</style>
```