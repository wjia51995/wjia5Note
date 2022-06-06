# 原型

![原型链1](image/JS/原型链1.webp)

​	在JavaScript中，每个函数都有一个prototype属性，这个属性是构造函数构造出来的实例的原型，即

````javascript
person.__proto__ == Person.prototype
````

该属性值默认是一个空对象（没有我们自行添加的属性值，有默认属性值），对象中的属性和方法会被person继承。

该对象中的constructor属性指向函数（构造函数Person()）本身，并且该对象指向函数的原型对象，即object.prototype，例如（即object()的prototype属性）

````javascript
Person.prototype.__proto__ == object.prototype
````

例中object.prototype即为构造函数object()的prototype属性，同样object.prototype中的属性和方法会被构造函数Person()继承，并且同样的,object.prototype中的constructor指向object()

# 原型链

​	又图中相互关联的原型组成的链状结构就是原型链，就是图中蓝色这条线。当从person中找不到某个属性就会从person的原型``person.__proto__``也就是``Peson.prototype``中查找，再找不到继续往``Person.prototype.__proto__``中查找，直到最后若找到null即返回undifined。0

# 补充 

* `prototype`属性为显式原型，`__proto__`为隐式原型
* 函数的显示原型指向的对象（即引用的地址）默认是空Object实例对象（但Object的显示原型不然，即Object.prototype不是Object的实例）
* Object的原型对象是原型链的尽头，即`Object.prototype.__proto__`为null
* 所有函数都是Function的实例（包括Function本身），即`Person.__proto__`都指向`Function.prototype`，且`Function.prototype`是Object()的实例，即`Function.prototype.__proto__ === Object.prototype`
* 特别注意Object()本身是Function()的实例，因此`Object.__proto__ === Function.prototype`

![原型链图](image/JS/原型链图.png)

**注意图中绿色部分，即Function()是构造函数Function的实例，即Function()是自身的实例。**

# instanceof

* instanceof 是如何判断的？
  * 表达式： A instanceof B
  * 如果B函数的显示原型对象（B.prototype）在A对象的原型链上，返回true，否则返回false 
* Function是通过new自己产生的实例

# 继承实现方式