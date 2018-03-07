# 01-总体架构

** jQuery 使用上的几大特点：**
1. $('#id') 函数方式直接生成jQuery对象
2. $('#id').css().html().hide() 链式调用

## 无 new 函数实现

我们知道实例化对象都需要new，但是jQuery没有。
直$('#id')就生成了jQuery对象。 


这个代码思路不错，return直接用new jQuery，但是结果。。。
会一直在控制台打印hello
```js
var jQuery = function () {
    console.log('hello');
    return new jQuery();
};
jQuery();
```
