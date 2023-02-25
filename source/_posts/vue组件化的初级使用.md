---
title: vue组件化的初级使用
date: 2022-06-22 16:15:14
tags: Vue
categories: note
# 加入时间线
selected: true
---

# vue的组件化的初级使用
## 1.创建组件构造器对象：
``` js
const cpn = Vue.extend({
    template:`
            <div>
                <h2>我是标题</h2>
                <p>我是内容1</p>
                <p>我是内容2</p>
            </div>
            `
})
```

## 2.注册组件
``` js
// 1.全局组件的注册方法，可以在多个Vue实例下使用
// Vue.component('组件的标签名',组件名)
Vue.component('my-cpn',cpn)


// 2.局部注册组件，在构建的new Vue中使用components属性注册
const app = new Vue({
    el:'#app',
    components:{
        // 组件的标签名: 组件名
        my-cpn2: cpn
    }
})
```

## 3.使用组件
在el绑定的div中使用组件
``` html
<div id='app'>
    <my-cpn></my-cpn>
    <my-cpn2></my-cpn2>
</div>
```