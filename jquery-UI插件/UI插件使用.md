# 1. jquery-UI 插件使用步骤

> 备注：页面 jQuery.js 的引用位置问题,如果导入了其它与 jquery 有关的 js 文件,那么 jquery.js 须在其它 js 的前面`https://blog.csdn.net/xyffly/article/details/73555648`（所以下面的第二步和第三步的引入顺序不能变）

- **_第 1 步_**：引入官网 jquery-ui 的 css 样式文件
- **_第 2 步_**：引入官网 jquery 的 js 库
- **_第 3 步_**：引入官网 jqueryUI 的 js 库文件
- **_第 4 步_**：使用 jqueryUI 的功能
+ 具体操作：
    - 打开官网的ui插件的index.html，然后查看后台查找指定元素直接复制到自己的html网页就可以(包含样式代码和jquery代码和html元素代码)
    - 复制的jquery代码需要使用jquery全局加载包着：`$(function() {});`
```html
<!-- 示例1：slider功能 -->
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

```html
<!-- 示例2：dialog功能 -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>

    <link rel="stylesheet" href="jquery-ui-1.12.1.custom/jquery-ui.css" />
    <!-- 如果导入了其它与jquery有关的js文件,那么jquery.js须在其它js的前面 -->
    <script src="jquery-3.4.1/jquery-3.4.1.js"></script>
    <script src="jquery-ui-1.12.1.custom/jquery-ui.min.js"></script>
    <style>
        #dialog-link {
		padding: .4em 1em .4em 20px;
		text-decoration: none;
		position: relative;
	}
	#dialog-link span.ui-icon {
		margin: 0 5px 0 0;
		position: absolute;
		left: .2em;
		top: 50%;
		margin-top: -8px;
	}
    </style>
    <script>
      // Link to open the dialog
      $(function() {
        $( "#dialog" ).dialog({
            autoOpen: false,
            width: 400,
            buttons: [
                {
                    text: "Ok",
                    click: function() {
                        $( this ).dialog( "close" );
                        if($("#userName").val() == "xiaomei") {
                            alert("登录成功了");
                        }else{
                            alert("fail");
                        }
                    }
                },
                {
                    text: "Cancel",
                    click: function() {
                        $( this ).dialog( "close" );
                    }
                }
            ]
        });
        $("#dialog-link").click(function(event) {
          $("#dialog").dialog("open");
          event.preventDefault();
        });

        $("#dialog-link").hover(
          function() {
            $(this).addClass("ui-state-hover");
          },
          function() {
            $(this).removeClass("ui-state-hover");
          }
        );
      });
    </script>
  </head>
  <body>
        <h2 class="demoHeaders">Dialog</h2>
        <p>
            <button id="dialog-link" class="ui-button ui-corner-all ui-widget">
                <span class="ui-icon ui-icon-newwin"></span>Open Dialog
            </button>
        </p>
        <!-- ui-dialog -->
<div id="dialog" title="Dialog Title">
    登录:<input type="text" id="userName"><br>
    密码:<input type="text"id="passwd">
</div>

</html>

```
