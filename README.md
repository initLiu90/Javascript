# 1. Apply方法的polyfill：
```javascript
function myApply(obj, args) {
    let context = obj || window;
    context.fn = this;
    if (!args) {
      context.fn();
    } else {
      if (!args instanceof Array) {
        throw new Error("params must be array");
      } else {
        context.fn(...args);
      }
    }
    delete context.fn;
  }
  
  Function.prototype.myApply = myApply;
  
  var obj = {
    a: 2,
  };
  
  function foo() {
    console.log(this.a);
  }
```