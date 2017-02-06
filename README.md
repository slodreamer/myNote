# myNote
## 单体设计模式
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
