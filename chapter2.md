## init 构造器
---

### 为何jQuery可以这样写？

链式调用的好处，就是写出来的代码非常简洁，而且代码返回的都是同一个对象，提高代码效率。

```js
$('#id').css().html().hide()
```

### 核心就在return this
```js
init: function (selector) {
    var ele = document.querySelectorAll(selector);
    // 把 this 当作数组，每一项都是 DOM 对象
    for (var i = 0; i < ele.length; i++) {
        this[i] = ele[i];
    }
    //为循环用的
    this.length = ele.length;
    //返回这个this数组
    return this;
},
css: function (attr, val) {
    for (var i = 0; i < this.length; i++) {
        this[i].style[attr] = val;
    }
},
```

