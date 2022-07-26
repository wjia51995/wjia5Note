##### 1.html5新增内容

- 新的语义元素，比如 `<header>`, `<footer>`, `<article>`, and` <section>`。
- 新的表单控件，比如数字、日期、时间、日历、系统选色器和滑块。
- 强大的图像支持（借由1` <canvas>` 和` <svg>`）
- 强大的多媒体支持（借由 `<video>` 和 `<audio>`）
- 强大的新 API，比如用本地存储取代 cookie。

###### 1.1 html5新语义标签

* header：页眉
* footer：页脚
* main：主体

以上三个标签在一个网页中只能出现一次

* hgroup：标题组合（包含h1、h2等标题标签）
* nav：导航
* article：独立的内容
* aside：辅助信息的内容（侧边栏）
* section：区域（可嵌套在article中）
* figure：描述图像或视频
* figcaption：描述图像或视频的标题部分
* datalist：选项列表
* details/summary：文档细节/文档标题
* progress/meter：定义进度条/定义度量范围
* time：定义日期或时间
* mark：带有记号的文本

```html
<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <title>Demo</title>
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <style type="text/css">
    * {
      /*初始化样式*/
      margin: 0;
      padding: 0;
    }
    html {
      /*用于 获取 屏幕的可视宽高*/
      width: 100%;
      height: 100%;
      overflow: hidden;
    }
    body {
      /*让 body 初始 width 和 height 就 等于 页面可视区域的 宽高*/
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
 
      /*用于 测试的 样式*/
      background-color: #444;
      color: #FFF;
      letter-spacing: 4px;
      font-size: 28px;
      /*文字居中*/
      display: flex;
      justify-content: center;
      align-items: center;
    }
    @media screen and (orientation:portrait) {
      /*竖屏样式*/
      body {
        transform-origin: 0 0;
        transform: rotateZ(90deg) translateY(-100%);
      }
    }
    /*测试 边边角角*/
    div {
      background-color: #F00;
      position: fixed;
      height: 2px;
      width: 100px;
    }
    div:nth-of-type(1){
      top: 0;
      left: 0;
    }
    div:nth-of-type(2){
      top: 0;
      right: 0;
 
    }
    div:nth-of-type(3){
      bottom: 0;
      left: 0;
    }
    div:nth-of-type(4){
      bottom: 0;
      right: 0;
    }
  </style>
</head>
<body>
  Loading2
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <script>
    (function () {
      function resize() {
        var body = document.getElementsByTagName('body')[0];
        var html = document.getElementsByTagName('html')[0];
        var width = html.clientWidth;
        var height =  html.clientHeight;
        var max = width > height ? width : height;
        var min = width > height ? height : width;
        body.style.width = max + "px";
        body.style.height = min + "px";
      }
      resize();
      window.addEventListener("resize", resize)
    })();
  </script>
</body>
</html>
```

