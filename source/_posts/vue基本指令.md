---
title: vue基本指令
date: 2022-05-05 08:50:14
tags: Vue
categories: note
# 加入时间线
selected: true
---

# Mustache语法：{ { message } }

# vue基础数据 👇
``` js
<script>
    const app = new Vue({
        el: '#app',
        data:{
            message: 'Hello Vue!',
            url: '<a href="http://www.baidu.com">百度一下</a>',
            num: 0,
            imgUrl: 'https://z3.ax1x.com/2021/08/16/f2Hzo6.png',
            movies:['哈利波特','钢铁侠','海上钢琴师','蜘蛛侠']
        }
    });
</script>
```

## v-once
"v-once" ：数据只渲染一次，不随着数据变化而变化。
``` html
<div id="app" v-once>{{message}}</div>
```

## v-html
"v-html" ：解析服务器返回的数据，并以链接的形式在dom上展示
``` html
<div id="app" v-html="url"></div>
```

## v-text
"v-text" ：与{{message}}效果一致，但无法在后面拼接文本
``` html
<div id="app" v-text="message">此处拼接文本无效</div>
```

## v-pre
"v-pre" ：不解析，直接显示
``` html
<div id="app" v-pre>{{message}}</div>
```

## v-cloak
"v-cloak" ：在vue未加载时，隐藏该元素
``` html
<div id="app" v-cloak>{{message}}</div>
```

## v-on
"v-on" ：元素操作控制，v-on:操作="函数"
``` html
<div id="app">
    <h2>{{num}}</h2>
    <button v-on:click="add">+</button> <!-- 常规写法 -->
    <button @click="add">+</button> <!-- 语法糖写法 -->
</div>
```

## v-for
"v-for" ：循环
``` html
<div id="app">
    <ul>
        <!-- v-for="自定义名称 in 循环对象名称" -->
        <!-- v-for="(自定义名称, index) in 循环对象名称"，index可以遍历数组下标 -->
        <li v-for="item in movies"></li>
    </ul>
</div>
```

## v-bind
"v-bind" ：绑定元素属性，直接调用服务器返回的数据进行动态展示
``` html
<div id="app">
    <img v-bind:src="imgUrl" alt=""> <!-- 常规写法 -->
    <img :src="imgUrl" alt=""> <!-- 语法糖写法 -->
</div>
```

"v-bind"对象语法：
``` html
<!-- css部分 -->
<style>
    .active{color: skyblue;}
    .error{color: red;}
</style>
```
``` html
<!-- html部分 -->
<div id='app'>
    <!-- 单独绑定一个类 -->
    <h2 :class="active">{{message}} 1</h2>
    <!-- 使用方法，绑定多个类，并控制开关 -->
    <!--写法：v-bind:class="{类名1: bool值, 类名2: bool值}" -->
    <h2 :class="{active: isActive, error: isError}">{{message}} 2</h2>
    <!-- 用function方法获取class -->
    <h2 :class="getClass()">{{message}} 3</h2>
</div>
```
``` js
// js部分
<script>
    const app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!',
            active: 'active',
            isActice: 'true',
            isError: 'true'
        },
        methods: {
            getClass: function(){
                // 此处调用本对象app内的"isActive"和"isError"，需要指向"this"
                return {active: this.isActive, error: this.isError};
                // 返回值 {active: isActive, error: isError}
            }
        }
    })
</script>
```

v-bind数组语法：
``` html
<!-- html部分 -->
<div id="app">
    <!-- 使用数组作为类名 -->
    <h2 :class="[active,error]">{{message}}</h2>
    <h2 :class="getClass()">{{message}}</h2>
</div>
```
``` js
// js部分
<script>
    const app = new Vue({
        el: #app,
        data: {
            message: 'Hello Vue',
            active: 'aaa',
            error: 'bbb'
        },
        methods: {
            getClass: function(){
                return [this.active, this.error];
            }
        }
    });
</script>
```