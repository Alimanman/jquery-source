# 01-总体架构

** jQuery 使用上的几大特点：**
1. $('#id') 函数方式直接生成jQuery对象
2. $('#id').css().html().hide() 链式调用

## 无 new 函数实现

我们知道实例化对象都需要new，但是jQuery没有。
直$('#id')就生成了jQuery对象。 


这个代码思路不错，return直接用new jQuery，因为这样可以省略new。
```js
var jQuery = function () {
    console.log('hello');
    return new jQuery();
};
jQuery();//无限hello
```
但实际结果，会一直在控制台打印hello...
因为，第一次jQuery() 会创建一个 new jQuery()，new jQuery() 又会创建一个 new jQuery()...

> 从前有座山山里有座庙庙里有个老和尚...

递归啊。。。有没有

###如何停止循环
```js
var jQuery = function () {
    console.log('hello');
    return new jQuery.prototype.init();
};
jQuery.prototype = {
    init: function () {
        console.log('init');
    }
};
jQuery();//hello
         //init
```
