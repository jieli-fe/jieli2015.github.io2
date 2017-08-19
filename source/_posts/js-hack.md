---
title: js 的浏览器兼容
date: 2017-07-27 09:44:46
tags: js兼容
---
`js`的兼容总结



##### getElementsByClassName
getElementsByClassName()方法在几个重要的浏览器中支持的最低版本:

浏览器 | 最低版本
--- | ---
谷歌 | 4.0
IE | 9.0
火狐 | 3.0

```javascript
//兼容写法
function getClassName(name){
    if(!name) return []
    if(document.getElementsByClassName(name)){
        return document.getElementsByClassName(name)
    }else{
        var all = document.getElementsByTagName("*"),
        arr = [];
        for (var i = 0; i < all.length; i++){
            if(all[i].className = name){
               arr.push(all[i])
            }
        }
        return arr
   }
}
```

##### 事件的绑定
兼容写法
```js
/**
 * event 跨浏览器兼容写法
 * @method addEvent
 * @param  {[HTMLCollection]}   obj  [HTMLCollection对象]
 * @param  {[string]}   type [事件类型]
 * @param  {Function} fn   回调
 */
function addEvent(obj,type,fn){
    if (typeof obj.addEventListener != 'undefined') {
        return obj.addEventListener(type,fn,false);
    }else if(typeof obj.attachEvent != 'undefined'){
        retrun obj.attachEvent("on" + type, fn);
    }
}
```


##### event事件对象
关于获取鼠标坐标的详解参考[link](http://www.cnblogs.com/mmzuo-798/p/5533439.html) [link2](http://blog.csdn.net/lzding/article/details/45437707)
```js
document.onclick =  function (evt){
    var event = evt || window.event;
    console.log(event.clientX)
}
```

