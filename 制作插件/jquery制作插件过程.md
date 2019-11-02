# 1. 原始

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>插件制作过程1</title>
    <style>
      .cls {
        width: 200px;
        height: 200px;
        margin-top: 30px;
        margin-left: 30px;
        background-color: pink;
        float: left;
      }
    </style>
    <script src="jquery-3.4.1/jquery-3.4.1.min.js"></script>
    <script>
      $(function() {
        $("input[type=button]").click(function() {
          $(".cls").css("backgroundColor", $(this).val());
        });
      });
    </script>
  </head>
  <body>
    <input type="button" value="blue" />
    <input type="button" value="red" />
    <input type="button" value="green" />
    <div id="box">
      <div class="cls"></div>
      <div class="cls"></div>
      <div class="cls"></div>
    </div>
  </body>
</html>
```

# 2. 过渡阶段

## 2.1 过渡 1

- 独立功能提取成函数

```html
<script>
  $(function() {
    $("input[type=button]").click(function() {
      // $(".cls").css("backgroundColor", $(this).val());
      changeColor($(this).val());
    });
  });
  function changeColor(color) {
    $(".cls").css("backgroundColor", color);
  }
</script>
```

## 2.2 过渡 2

- 独立功能函数注册到 jquery 中；使得每个 jquery 元素对象都可以直接调用使用
- 这种制作的插件都是需要对特别的 css 和 html 和 js 使用，所以需要附上使用教程

```html
<script>
  // $.fn.xxx = function 注册函数固定写法
  $.fn.changeColor = function(color) {
    $(".cls").css("backgroundColor", color);
  };
  $(function() {
    $("input[type=button]").click(function() {
      // jquery元素对象直接使用
      $(".cls").changeColor($(this).val());
    });
  });
</script>
```

# 3 制作过程
## 3.1 css提取
+ 将如下的css提取到changeColor.css
```css
.cls {
        width: 200px;
        height: 200px;
        margin-top: 30px;
        margin-left: 30px;
        background-color: pink;
        float: left;
    }
```
## 3.2 制作的jquery插件js提取
+ 将如下js提取到changeColor.js
```js
$.fn.changeColor = function(color) {
    $(".cls").css("backgroundColor", color);
};
```

# 4. 写插件使用教程

```js
// 步骤1：引入外部css样式文件
<link rel="stylesheet" href="changeColor.css">

// 步骤2：引入外部js
<script src="jquery-3.4.1/jquery-3.4.1.min.js"></script>
<script src="changeColor.js"></script>

// 步骤3：复制如下js代码到html
$(function(){
    $("input[type=button]").click( function(){
        $(".cls").changeColor($(this).val());
    });
});

// 步骤4：复制如下代码到body中
<input type="button" value="blue">
<input type="button" value="red">
<input type="button" value="green">
<div id="box">
    <div class="cls"></div>
    <div class="cls"></div>
    <div class="cls"></div>
</div>
```
