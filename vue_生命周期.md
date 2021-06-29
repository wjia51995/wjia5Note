# 生命周期

## beforeCreate()

​	vue的第一个生命周期，该周期中data和methods中的数据都还没有初始化

## created()

​	如果要调用methods中的方法，或者操作data中的数据，最早只能在created中操作

接着判断有无“el” option，有则进行下一步，即判断有无“template” option，没有“template” option则进行`Compile el's outerHTML as template`  有则进行 `Compile template into render function`，该部分作用如下：

created()生命周期后vue开始编译模板，把vue代码中的指令进行执行，最终在内存中生成一个编译好的模板字符串，接着把该字符串渲染为内存中的DOM，此时只是在内存中渲染好了模板，并没有把模板挂载到真正的页面中去

## beforeMount()

​	模板已经在内存中编译完成了，但是尚未把模板挂载到页面中，此时页面还是旧的

接着`Create vm,$el and replace "el" with it` 即将内存中编译好的模板，真实地替换到浏览器页面中去

## mounterd()

​	内存中的模板，已经真实地挂载到页面中，用户已经可以看到渲染好的页面了，若要通过某些插件操作页面上的DOM节点，最早要在mounted中进行。该周期表示vue实例已经初始化完毕

## beforeUpdate()

​	只有当数据改变时才会触发，该生命周期中，页面中显示的数据还是旧的，但此时data数据已经更新，页面尚未和最新的数据保持同步。

接着执行`Virtual DOM re-render and path` 即先根据data中最新的数据，在内存中重新渲染出一份最新的内存DOM树，当最新的内存DOM树被更新之后，会把最新内存的DOM树重新渲染到真实的页面中去，这时候完成了数据从data（Model层）-> view（视图层）的更新

## updated()

​	该生命周期内，页面和data数据已经保持同步了

## beforDestroy()

​	当执行beforDestroy()时，实例上所有的data和所有的methods以及过滤器、指令等都仍然可用，此时还未进行销毁

## destroy()

​	组件已经被完全销毁