---
title: JavaScript中__proto__与prototype
date: 2021-05-03 02:02:37
tags: JavaScript
categories: JavaScript
---

*概要：js中\_\_proto\_\_和prototype的区别与个人解读*

<!--more-->

#### 关于js中_\_proto\_\_和prototype的说明

##### 区别：

 \_\_proto\_\_是浏览器对实例化对象中[[prototype]]属性的命名，_\_proto\_\_是属于对象的属性，prototype是属于函数对象的属性。

##### 功能：

\_\_proto\_\_是访问prototype的入口。

#### 个人解读：

##### 区别：

prototype可以理解为在函数（函数对象）上的一个名为叫原型对象的属性，这里的原型对象是命名和功能意义双重含义的，所以prototype是函数（函数对象）上的一个属性，保存原型对象，意义上也可以叫做原型对象。那么这个原型对象的内容是一些可以继承的属性和方法。而\_\_proto\_\_是对象上的一个属性，通过这个属性可以访问prototype这个函数对象上的属性里的内容，也就是说`对象.__proto__`指向构造该对象的`函数.prototype`。

比如：

```js
function Fn1(...){...}; //构造函数
let obj1 = new Fn1(...); //new一个对象
obj1.__proto__ === Fn1.prototype; //true
```

当然，由于函数在js语言中也是对象，所以也有\_\_proto\_\_属性，指向构造该函数的函数的prototype，一次类推，这就形成了一条原型链，链子的尽头是Object.prototype为null，这个Object非泛指某一个对象，而是实际的构造所有对象的函数。

##### 补充：

这里还要提一下construct这个属性，理解为构造器，该属性是函数，并挂载在函数的prototype属性上。每一个由函数构造而来的对象都有一个construct属性（继承于构造该对象的函数），该属性功能为访问（获取）构造该对象的构造函数，可以理解为`该构造函数.prototype.construct == 该构造函数`。<span style="color:red">该构造函数构造的对象.construct</span>继承自<span style="color:red">该构造函数.prototype.construct</span> == <span style="color:red">该构造函数</span>

