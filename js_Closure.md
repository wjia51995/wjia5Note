# 满足以下特点的 叫做闭包：

​	1、函数嵌套函数

​	2、内部函数使用外部函数的形参和变量

​	3、被引用的形参和变量就不会被垃圾回收机制所回收

# 闭包的好处

​	1、变量可以常驻在内存中

​	2、避免全局变量污染，避免声明全局变量

​	3、可以声明私有成员

## 实现：1、避免全局污染	2、对a进行累加	【注】让a变量常驻内存 （需要用闭包）

普通函数写法：

````javascript
function aaa(){
    var a = 2;
    function bbb(){
        a++;
        alert(a);
    }
    return bbb;
}
var ccc = aaa()
ccc()
ccc()
alert(a)	// 报错，外部访问不到变量a
````

立即执行函数写法：

````javascript
var ccc = (function(){
    var a = 2;
    return function(){
        a++;
        alert(a);
    }
})();
ccc();
ccc();
alert(a);	// 报错，外部访问不到变量a
````

## 避免变量全局污染

​	A同学的代码：

````javascript
var moduleA = (function(){
	var count = 100;
	function aaa(){
		count += 2;
		alert(count);
	}
	function bbb(){
		count *= 10;
		alert(count);
	}
	return {
		funcA: aaa,
		funcB: bbb
	}
})();
````

B同学的代码：

````javascript
var moduleB = (function(){
	var count = 100;
	function aaa(){
		count += 5;
		alert(count);
	}
	function bbb(){
		count *= 20;
		alert(count);
	}
	return {
		funcA: aaa,
		funcB: bbb
	}
})();
````

````javascript
moduleA.funcA();
moduleA.funcB();
moduleB.funcA();
moduleB.funcB();
````

另一种向外暴露对象写法：

```js
(function(){
	var count = 100;
	function aaa(){
		count += 5;
		alert(count);
	}
	function bbb(){
		count *= 20;
		alert(count);
	}
    window.myModule = {
        funcA: aaa,
		funcB: bbb
    }
})()
```

使用闭包要注意及时释放闭包的内存，不然容易造成内存溢出和内存泄漏。

1.内存溢出：

​	一种程序运行出现的错误；

​	当程序运行需要的内存超过了剩余的内存时，就会抛出内存溢出的错误。

2.内存泄漏：

​	占用的内存没有及时释放；

​	内存泄漏积累多了就容易导致内存溢出；

​	常见的内存泄漏：意外的全局变量；没有及时清理的计时器或回调函数；闭包。
