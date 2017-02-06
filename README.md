# myNote
## 单体设计模式
### 惰性加载
单体对象都是在脚本加载时被创建出来.对于资源密集型的域配置开销大的单体,也许更合理的做法是将其实例化推迟到需要使用它的时候.这种技术被称为惰性加载.个人理解:所谓的惰性加载就是把他包含在函数中,当你使用时就去调用它然后才实例化对象.因为没有实例化的对象是不占内存空间的.
单体模式在js中的实现有两种方式。一，对象字面量。二，闭包。

1. 对象字面量方式（可以避免意外重写变量）
```js
var name = 'lj'
var singleTon = {
  name: 'lll',
  getName: function() {
    alert(this.name)
    alert(singleTon.name)
  }
}
```
```js

var MyNamespace = {}
MyNamespace.singleTon = (function () {
  var instance
  function Constructor () {
    var attr = 2
    function privateMethod () {
      return '私有函数'
    }
    return  {
      publicMethod: function () {
        return privateMethod()
      },
      publicMethod1: function () {
        return attr
      }
    }
  }
  return {
    getInstance: function () {
      if (!instance) {
        console.log('11111111')
        instance = Constructor()
      }
      return instance
    }
  }
})()

MyNamespace.singleTon.getInstance().publicMethod() // '私有函数'
```
