<!--
 * @Description: file content
 * @Author: wanghaoyu
 * @Date: 2023-10-25 21:01:41
 * @LastEditors: wanghaoyu
 * @LastEditTime: 2023-10-25 21:42:00
-->
# 前端常用手写工具函数

## 原生方法实现
### Object.create
```javascript
function ObjectCreate(obj) {
  function F() {}
  F.prototype = obj
  return new F();
}
```
### instanceof
```javascript
  function myInstanceof(obj1, obj2) {
    let proto = Object.getPrototypeOf(obj1);
    let prototype = obj2.prototype;
    while(true) {
      if (!proto) return false;
      if (proto === prototype) return true;
      proto = Object.getPrototypeOf(proto);
    }
  }
```

## 闭包相关
**闭包实际上是一种函数**，闭包就是也是函数技术的一种；闭包能做的事情函数几乎都能做。
闭包也可认为是一种作用域。
闭包技术花式比较多，用法也比较灵活，因为闭包技术的分界线并不明显，几乎无法用一个特点去区分。
闭包产生的时机：**内层的作用域访问它外层函数作用域里的参数/变量/函数**时，闭包就产生了。
闭包的不足：由于闭包会引用它外层函数作用域里的变量函数，因此，会比其他非闭包形式的函数占用更多内存，当外层函数执行完毕退回函数调用栈（call stack）的时候，外层函数作用域里变量因为被引用着，可能并不会被引擎的垃圾回收器回收，因而会引起内存泄漏。过度使用闭包会导致内存占用过多，甚至内存泄漏。
### 单例模式
单例模式，应用与该实例在某个条件下多次初始化使用缓存。
```javascript
const single = (() => {
  let current = null;
  // 函数通过参数传入
  return function (consturtor, ...arg) {
    if (!current) {
      current = new consturtor(...arg);
    }
    return current;
  }
})();
function testSingle() {
  this.a = 123;
}
const singletest = single(testSingle);
const singletest2 = single(testSingle);
console.log(singletest === singletest2); // true
```

### 节流&防抖
在搜索类场景下常用节流，在用户滚动屏幕下常用防抖；及节流为停止后触发，防抖为定时触发；
```javascript
// 节流
const throttle = (() => {
  let current = null;
  return function (fn, time = 1000) {
    if (current) {
      clearTimeout(current);
      current = null;
    }
    current = setTimeout(fn, time);
  }
})();
// 防抖
const debounce = (() => {
  let current = null;
  return function(fn, time) {
    if (current) {
      current = setTimeout(() => {
        fn();
        current = null;
      }, time);
    }
  }
})();
```

### 
