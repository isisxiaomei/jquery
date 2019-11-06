# 1. jquery-UI 插件使用步骤

> 备注：页面 jQuery.js 的引用位置问题,如果导入了其它与 jquery 有关的 js 文件,那么 jquery.js 须在其它 js 的前面（所以下面的第二步和第三步的引入顺序不能变）

- **_第 1 步_**：引入官网 jquery-ui 的 css 样式文件
- **_第 2 步_**：引入官网 jquery 的 js 库
- **_第 3 步_**：引入官网 jqueryUI 的 js 库文件
- **_第 4 步_**：使用 jqueryUI 的功能
- 参考：https://blog.csdn.net/xyffly/article/details/73555648

```html
<!-- 示例1：
打开官网的ui插件的index.html，然后查看后台查找指定元素直接复制到自己的html网页就可以
 -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>

    <link rel="stylesheet" href="jquery-ui-1.12.1.custom/jquery-ui.css" />
    <!-- 如果导入了其它与jquery有关的js文件,那么jquery.js须在其它js的前面 -->
    <script src="jquery-3.4.1/jquery-3.4.1.js"></script>
    <script src="jquery-ui-1.12.1.custom/jquery-ui.min.js"></script>
    <script>
      $(function() {
        $("#slider").slider({
          range: true,
          values: [17, 67]
        });
      });
    </script>
  </head>
  <body>
    <!-- Slider -->
    <h2 class="demoHeaders">Slider</h2>
    <div id="slider"></div>
  </body>
</html>
```
