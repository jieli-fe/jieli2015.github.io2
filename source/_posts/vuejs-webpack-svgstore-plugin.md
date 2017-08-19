---
title: vuejs&&webpack-svgstore-plugin
date: 2017-08-10 21:55:00
tags: vue webpack svg
---
### vuejs 使用svgsprite做icon的配置

首先看[官网](https://www.npmjs.com/package/webpack-svgstore-plugin)

##### 安装
```shell
npm i webpack-svgstore-plugin --save-dev
```
<!-- more -->
##### 注意下兼容问题
node兼容
仅支持
- "7.0+"
- "6.0"
- "4.0"

webpack的兼容
- Use webpack-svgstore-plugin@3.x.x for Webpack 1.x.x
- Use webpack-svgstore-plugin@4.x.x for Webpack 2.x.x

##### 怎么使用？？
```javascript
//webpack.config.js
var SvgStore = require('webpack-svgstore-plugin');
module.exports = {
  plugins: [
    // create svgStore instance object
    new SvgStore({
      // svgo options
      svgoOptions: {
        plugins: [
          { removeTitle: true }
        ]
      },
      prefix: 'icon'
    })
  ]
}
```
1. 导入svg plugin
```javascript
var SvgStore = require('webpack-svgstore-plugin');
```
2. 创建实例对象
```javascript
new SvgStore({
  // svgo options
  svgoOptions: {
    plugins: [
      { removeTitle: true }
    ]
  },
  prefix: 'icon'
})
```
3. 导入svgRtore
注意下路径， path是存放svg目录， name是导出的svg路径和名称。
```javascript
var __svg__           = { path: './assets/svg/**/*.svg', name: 'assets/svg/[hash].logos.svg' };
require('webpack-svgstore-plugin/src/helpers/svgxhr')(__svg__);
```

4. 使用
在vuejs中的template中使用
```javascript
<template>
  <svg style='font-size: 12px'>
    <use :xlink:href="#icon-add"></use>
  </svg>
</template>
```
##### 注意事项
assets 文件夹内的svg `请统一小写命名`

##### 结语
自己琢磨的，写的不好请见谅。有啥错误支持请指正！
