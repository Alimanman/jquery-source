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
