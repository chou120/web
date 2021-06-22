






1、初识HTML
HyperTextMarkupLanguage（超文本标记语言）

< body >、< /body>等成对的标签，分别叫做开放标签和闭合标签，

单独呈现的标签（空元素），如< hr/ >;意为用/来关闭空元素。

html注释：< !–注释内容–>


<!--DOCTYPE：告诉浏览器使用什么规范（默认是html）-->

<!DOCTYPE html>
<!--语言 zh中文 en英文-->
<html lang="zh">
<!--head标签代表网页头部-->
<head>
<!--    meta 描述性标签，表示用来描述网站的一些信息-->
<!--    一般用来做SEO-->
    <meta charset="UTF-8">
    <meta name="keywords" content="hyx的java学习">
    <meta name="description" content="一起来学习java">
    <!--网站标题-->
    <title>Title</title>
</head>
<!--body代表主体-->
<body>
Hello World！
</body>
</html>

## 2、网页基本标签

- 标题标签
- 段落标签
- 换行标签
- 水平线标签
- 字体样式标签
- 注释和特殊符号

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>基本标签</title>
</head>
<body>
<h1>一级标签</h1><!--标题标签-->
<h2>二级标签</h2>
<h3>三级标签</h3>
<h4>四级标签</h4>
<h5>五级标签</h5>
<h6>六级标签</h6>
    
<!--段落标签-->
<p>p换行1</p>
<p>p换行2</p>

<hr/><!--水平线标签-->

换行1 <br/><!--换行标签-->
换行2 <br/>
<!--换行标签比较紧凑，段落标签有明显段间距-->
<!--粗体 斜体-->
<h1>字体样式标签</h1>
粗体：<strong>I love you </strong><br/>
斜体：<em>I love you </em><br/>
<!--特殊符号-->
空格：1&nbsp;2&nbsp;&nbsp;3&nbsp;&nbsp;&nbsp;4<br/>
空格：1 2  3   4<br/>
大于号&gt;<br/>
小于号&rt;<br/>
版权符号&copy;<br/>
<!--特殊符号记忆：&开头;结尾，只要在idea中&敲出后就有提示-->
</body>
</html>

```

- 图像标签

- 链接标签

  **href**： 必填，表示要跳转到那个页面
  **target**：表示窗口在那里打开
  **_blank**：在新标签中打开
  **_self**： 在自己的网页中打开

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>图像和链接标签</title>
</head>
<body>
<!--src:资源地址
    相对地址，绝对地址
    ../上级地址
    alt：在图片加载失败的时候，就会用文字代替
    title:鼠标悬停在图片上时，所显示的名字
    width height 图片的高和宽-->
<img src="../xxx.jpg" alt="oops!图像不见了" title="123">
<br/>
<!--href：跳转页面的地址
    a标签内文字：即显示的文字
    可以把图片放在a标签内，点击图片跳转网页
    target:表示在哪打开新网页_self:当前标签打开 _blank:新的页面中打开-->
<a href="https://www.baidu.com" target="_blank" title="123">你xxxx不会百度吗</a>
<br/>
<a href="https://www.baidu.com"><img src="../xxx.jpg" alt="oops!图像不见了"></a>
    
<!--锚链接
    1.需要一个标记锚
    2.跳转到标记
    #页面内跳转-->
<a name="top"></a>
<a href="#top">回到顶部</a>
<br/>
<!--也可以在网址后添加#号跳到对应网站的对应位置-->
<a href="https://www.baidu.com#down">百度底部</a> <br/>
    
<!--功能性链接
邮箱链接：mailto
qq链接
-->
<a href="mailto:xxxxxxqq.com">点击联系我</a>
<a target="_blank"
   href="http://wpa.qq.com/msgrd?v=xxx&uin=&site=qq&menu=yes"/>
    <a target="_blank"
   href="http://wpa.qq.com/msgrd?v=xxx&uin=&site=qq&menu=yes">
    <img border="0" src="http://wpa.qq.com/pa?p=2::52" alt="点击这里加我领取小电影"
         title="点击这里加我领取小电影"/>
</body>
</html>


```

![image-20210622124213517](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210622124213517.png)

## 3、列表标签

### 什么是列表

列表就是信息资源的一种展示形式。它可以使信息结构化和条理化，并以列表的样式显示出来，以便浏览者能更快捷地获得相应的信息。

### 列表的分类：

- **无序列表**

<ol>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ol>

- **有序列表**

<ul><!--无序列表-->
    <li>123
        <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        </ul>
    </li>
    <li>2</li>
    <li>3</li>
</ul>

- **定义列表**

<!--自定义列表
dl：标签
dt：列表名称
dd：列表内容-->

<dl>
    <dt>学科</dt>
    <dd>语文</dd>
    <dd>数学</dd>
    <dd>英语</dd>
    <dt>语言</dt>
    <dd>中文</dd>
    <dd>英语</dd>
    <dd>日语</dd>
</dl>

## 4、表格

### 表格的基本结构：

- 单元格
- 行
- 列
- 跨行
- 跨列

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格</title>
</head>
<body>
    <!--表格table
    行 tr
    列 td
    -->
<table border="1px">
    <tr><!--跨列-->
        <td colspan="3">1-1</td>
    </tr>
    <tr><!--跨行-->
        <td rowspan="2">2-1</td>
        <td>2-2</td>
        <td>2-3</td>
    </tr>
    <tr>
        <td>3-2</td>
        <td>3-3</td>
    </tr>
</table>
</body>
</html>

## 5、视频和音频

- video
- audio

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>媒体元素</title>
</head>
<body>
<!--视频
		src 资源路径
        controls 控制面板
        autoplay 自动播放
-->
<video src="xxx/xxx/xxx" controls autoplay></video>
<!--音频-->
<audio src="xxx/xxx/xxx" controls autoplay></audio>
</body>
</html>

## 6、页面结构

| 元素名  | 描述                                               |
| ------- | -------------------------------------------------- |
| header  | 标题头部区域的内容（用于页面或者页面中的一块区域） |
| footer  | 标记脚部区域的内容（用于整个页面或页面的一块区域） |
| section | Web页面中的一块独立区域                            |
| article | 独立的文章内容                                     |
| aside   | 相关内容或应用                                     |
| nav     | 导航类辅助内容                                     |

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>页面结构</title>
</head>
<body>
<!--页面头部-->
<header>
    <h2>网页头部</h2>
</header>
<section>
    <h2>网页主体</h2>
</section>
<footer>
    <h2>网页脚部</h2>
</footer>
</body>
</html>

## 7、iframe内联框架(可不讲)

```html
<iframe src="path" name="mainFrame" ></iframe>
1
```

- ifram标签，必须要有src属性即引用页面的地址
- 给标签加上name属性后，可以做a标签的target属性，即在内联窗口中打开链接

## 8、表单语法(重点)

from标签，action属性为所提交的目的地址，method选择提交方式
可以选择使用post或者get方式提交

- get效率高，但在url中可以看到提交的内容，不安全，不能提交大文件
- post比较安全且可以提交大文件

| 标签         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| input标签    | 大部分表单元素对应的标签有text、password、checkbox、radio、submit、reset、file、hidden、image和button，**默认为text**，可以提交用户名、密码等等 |
| select标签   | 下拉选择框                                                   |
| textarea标签 | 文本域                                                       |

属性	说明
type	指定元素的类型。text、password、checkbox、radio、submit、reset、file、hidden、image和button，默认为text
name	指定表单元素的名称（提交时所对应的key）
value	元素的初始值，radio必须提供
size	指定表单元素的初始宽度。当type为text或者password时，以字符为单位；其他type以像素为单位
maxlength	type为text或者password时，输入的最大字符数
checked	type为radio或者checkbox时，指定按钮是否被选中

| 属性       | 说明                                           |
| ---------- | ---------------------------------------------- |
| readonly   | 只读，不可更改                                 |
| disable    | 禁用                                           |
| hidden     | 隐藏，虽然不可见但是会提交                     |
| id         | 标识符，可以配合label的for属性增加鼠标的可用性 |
| placehoder | text 文字域等输入框内的提示信息                |
| required   | 不能为空                                       |
| patten     | 正则表达式验证                                 |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录注册</title>
</head>
<body>
<h1>注册</h1>
<!--表单from
        action：表单提交的动作，可以是交给一个网址，也可以是交给一个请求处理地址
        method：post get请求方式-->
<form action="xxx/xxx" method="get">
    <!--文本输入框：input type="text"-->
    <p>用户名：<input type="text" name="username" value="请输入用户名" maxlength="10" size="20"></p>
    <p>密&nbsp;&nbsp;&nbsp;码：<input type="password" name="password" placeholder="请输入密码" required="required"></p>
    <!--    submit提交表单，reset清空-->
    <p><input type="submit"> <input type="reset">
    </p>
    <!--    radio单选框标签 value即单选框的值，在提交时对应value
    name：单选框组名，在同一个组内的radio标签同时只能选中一个，name值在提交时对应key
    checked:默认被选中
    -->
    <p>性别：<input type="radio" value="boy" name="sex"/>
        <input type="radio" value="girl" name="sex"/>
    </p>
    <p>爱好：
        <input type="checkbox" value="b" name="hobby">打篮球
        <input type="checkbox" value="s" name="hobby">唱rap
        <input type="checkbox" value="d" name="hobby">跳舞
    </p>
    <p><input type="button" name="btn1" value="按钮上文字"><!--按钮-->

        <input type="image" src="xxx/xxx"><!--图片按钮默认是提交：和submit类似-->
    </p>
    <p><!--下拉框：selected:默认选项-->
        你来自：
        <select name="location">
            <option value="china">中国</option>
            <option value="us" selected>美国</option>
            <option value="japan">日本</option>
        </select>
    </p>

    <p><!--文本域-->
        反馈：
        <textarea name="text" id="10" cols="30" rows="10" >文本内容</textarea>
    </p>
    <p><!--文件域-->
        <input type="file" name="files">
        <input type="button" name="upload" value="上传">
    </p>
    <!--邮件：会简单验证是否是邮箱地址
		url：会简单验证是否是网络地址
        number：数字验证-->
    <p>邮箱：<input type="email" name="email">
        url：<input type="url"></p>

    <!--数字验证
           max最大数量
           min 最小数量
           step 每次点击增加或减少的数量-->
    <p>商品数量<input type="number" name="num" max="100" min="1" step="1"></p>
    <!--滑块-->
    <p>音量：<input type="range" min="0" max="100" name="voice" step="2"></p>
    <!--搜索框-->
    <p>搜索：<input type="search"></p>

    <p><!--增强鼠标可用性-->
        <label for="mark">你点我试试</label>
        <input type="text" id="mark">
    </p>
</form>
</body>
</html>

```

