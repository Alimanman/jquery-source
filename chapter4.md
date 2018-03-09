## Callbacks
---

回调对象，函数的一个统一管理的方法。

### 官方栗子

```js
// 这两个作为 callback 函数
function fn1( value ) {
  console.log( value );
}
 
function fn2( value ) {
  fn1("fn2 says: " + value);
  return false;
}

// 调用 jQuery 的 Callbacks 生成 callbacks
var callbacks = $.Callbacks();
callbacks.add( fn1 );

callbacks.fire( "foo!" );
// 'foo!'
 
callbacks.add( fn2 );
 
callbacks.fire( "bar!" );
// 'bar!'
// 'fn2 says: bar!'
```
通过add添加操作到队列当中，通过fire去执行这些操作。

### 模拟Callbacks函数

```js
var Callbacks = function () {
    var Cb = {
        callbacks: [],
        add: function (fns) {
            this.callbacks.push(fns);//获得的fn添加到callbacks数组内
            return this;
        },
        fire: function () {
            this.callbacks.forEach(function (fn) {
                fn();//遍历add里时添加来的fn，并运行
            });
            return this;
        }
    };
    return Cb;//返回对象
};

var cba = Callbacks();
cba.add(fn1);
cba.add(fn2);
cba.fire();//fn1 fn2
```


