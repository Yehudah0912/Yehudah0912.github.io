# CSS3笔记

## 将行内元素转换为块级元素



![image-20220130200455519](https://gitee.com/lvyehao/assets/raw/master/img/image-20220130200455519.png)

```css
a {
    /* 可以使用Emmet语法(快捷语法)*/
  width: 150px;
  height: 50px;
  /* 设置样式为无修饰 */
  text-decoration: none;
  /* 把行内元素a转换为块级元素 */
  display: block;
  /* 把块级元素div转换为行内元素 */
  display: inline;
}
```

## 文字垂直居中

**当行高等于容器高度实现文字垂直居中**

```css
/* 当行高等于容器高度时字体垂直居中 */
a {
  height: 50px;
  line-height: 50px;
}
```

## 背景属性

背景符合语法：`background：背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置`

背景图片：`background-image:none|url(url)`;

> 注意：**background-image**属性描述了元素的背景图像。实际开发常见于logo或者一些**装饰性的小图片或者是超大的背景图片**，**优点是非常便于控制位置**。(精灵图也是一种运用场景)

背景平铺：` background-repeat: repeat|no-repeat|repeat-x|repeat-y`;

背景图片位置： `background-position: x y`;

| 参数值   | 说明                                              |
| -------- | ------------------------------------------------- |
| length   | 百分数\|有浮点数字和单位标识符组成的长度值        |
| position | top\|center\|bottom\|left\|center\|right 方向名词 |

背景图像固定(背景附着)：`background- `属性设置背景图像是否固定或者随着页面的其余部分滚动。

语法：`background-attachment：scroll|fixed`

| 参数值 | 说明                               |
| ------ | ---------------------------------- |
| scroll | 背景图像是随对象内容滚动           |
| fixed  | 背景图像固定(不随页面的滚动而滚动) |

背景色半透明：`background：rgba(0,0,0,0.3)`

## CSS三大特性

CSS有三个非常重要的三个特性：层叠性、继承性、优先级。

### 层叠性

层叠性定义：相同的选择器设置了相同的样式，此时一个样式就会覆盖(层叠)另一个冲突的样式。层叠性主要解决样式冲突的问题。

样式冲突：遵循就近原则

### 继承性

子标签会继承父标签的某些样式，如文本颜色和字号

```html
<style>
  /* 父类样式 */
	div {
		color: red;
        /* font: 文字大小/行高 字体 */
        font： 12px/24px 'Microsoft YaHei';
        /* 1.5相当于当前元素文字大小的1.5倍 */
        font： 12px/1.5 'Microsoft YaHei';
		font-size: 14px;
	}
</style>
<body>
	<div>
    <!-- 子类继承 -->
		<p>龙生龙，凤生凤</p>
	</div>
</body>
```

### 优先级

当同一个元素指定多个选择器，就会有优先级的产生。

- 选择器相同，则执行层叠性。

- 选择器不同，则根据选择器权重执行

  | 选择器               | 选择器权重 |
  | -------------------- | ---------- |
  | 继承 或者 *          | 0，0，0，0 |
  | 元素选择器           | 0，0，0，1 |
  | 类选择器，伪类选择器 | 0，0，1，0 |
  | ID选择器             | 0，1，0，0 |
  | 行内样式style='' ''  | 1，0，0，0 |
  | ！important重要的    | ∞ 无穷大   |

  优先级注意点：

  1. 权重是由4组数字组成，但不会进位。
  2. 可以理解为类选择器永远大于元素选择器，id选择器永远大于类选择器，以此类推。
  3. 等级判断从左向右，如果某一位数值相同，则判断下一位数值。
  4. 可以简单记忆法：通配符和继承权重为0，标签选择器为1，类/伪类选择器为10，id选择器100，行内样式表为1000，!important无穷大。
  5. 继承的权重为0，父元素的优先级再高，通过继承传给子元素后优先级为0。



### 权重叠加

符合选择器会有权重叠加的问题

```css
/* ul li 权重 0，0，0，1 + 0，0，0，1 = 0，0，0，2 */
ul li {
	color: green;
}
/* li 权重 0，0，0，1 */
li {
	color: red;
}
```



注意：当样式层叠冲突的时候可以使用**权重叠加**来解决冲突。



## CSS盒子模型

### 盒子模型

页面布局学习三大核心，盒子模型，浮动和定位。学习好盒子模型能很好的实现页面布局。

网页布局的本质：利用CSS摆放盒子到相应的位置。

盒子模型：就是把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。CSS盒子模型本质上就是一个盒子，封装周围的HTML元素，它包括：边框、内边距、外边距和实际内容。

#### 边框(border)

border可以设置元素的边框。边框有三部分组成：**边框宽度(粗细) 边框样式 边框颜色**

**边框会影响盒子的实际大小**(添加10 px的边框会使盒子大出20 px)，**如果测量的时候包含了边框，则需要width/height减去边框高度。**

语法： `border: border-width || border-style || border-color`

属性简写：`border：1px solid red;`(没有顺序)



| 属性         | 作用                   |
| ------------ | ---------------------- |
| border-width | 定义边框粗细，单位是px |
| border-style | 边框的样式             |
| border-color | 边框颜色               |

边框分开写法：

`border-top: 5px solid red`(可以使用层叠性技巧)

相邻的两个边框合并在一起：`border-collapse:collapse`;(解决两个表格边框合并后原本1px的实线变成2px);

#### 内边距(padding)

padding属性用于设置内边距，即边框与 内容之间的距离。

`padding-top|padding-buttom|padding-left|padding-right`

设置padding属性会**撑大盒子大小**。

> 解决办法：
>
> - **不指定子元素盒子的宽度/高度**,当没有设置子元素的宽度时添加padding值不会大于父元素的宽度。
>
>   > 如果盒子本身没有指定width/height属性，则此时的padding不会撑大盒子的大小。
>
> - 使用**怪异盒模型**(新概念)`box-sizing:border-box`
>
> - **测量的时候包含了边距，则需要width/height减去边框高度**。



![image-20220207201310632](https://gitee.com/lvyehao/assets/raw/master/img/image-20220207201310632.png)

使用案例：

![image-20220207204434786](https://gitee.com/lvyehao/assets/raw/master/img/image-20220207204434786.png)

**可以使用padding撑开盒子的特性做很多事情**

新浪导航栏每个选项之间的间隔可以使用padding内边距来保持整体一致。

案例网址：https://yehudah0912.github.io/Sinanav.html

源代码：

```html
<!--
 * @Author: yehuda
 * @Date: 2022-02-07 21:18:25
 * @LastEditTime: 2022-02-07 21:34:14
 * @LastEditors: yehuda
 * @Description: 新浪网导航栏案例
 * @FilePath: \CSS\新浪网导航栏案例.html
-->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>新浪网导航栏案例</title>
  <style>
    body {
      margin: 0;
      padding: 0;
    }
    .nav {
      margin: 0;
      height: 41px;
      background-color: #fcfcfc;
      font-size: 12px;
      line-height: 41px;
      border-top: 3px #ff8500 solid;
      border-bottom: 1px solid #edeef0;
    }
    .nav a {
      height: 41px;
      /* a属于行内元素 此时必须要转换 行内块状元素 */
      display: inline-block;
      color: #4c4c4c;
      padding: 0 10px;
      text-decoration: none;
    }
    .nav a:hover {
      color: #ff8500;
      background-color: #eee;
    }
  </style>
</head>
<body>
  <div class="nav">
    <a href="#">设为首页</a>
    <a href="#">手机新浪网</a>
    <a href="#">移动客户端</a>
    <a href="#">微博</a>
    <a href="#">关于我</a>
  </div>
</body>
</html>
```



#### 外边距(margin)

margin属性用于设置外边距，即**控制盒子和盒子之间的距离**。

属性值：`margin-left||margin-right||margin-top||margin-bottom`

**块级盒子水平居中对齐**(常用-对行内元素或者块级元素无效)

语法：`margin：0 auto(水平居中)`

>注意：以上方法时让块级元素水平居中，**行内元素或者行内块状元素水平居中给其父元素添加`text-align:center`元素**

**嵌套块元素垂直外边距的塌陷**

对于两个嵌套关系(父子关系)的块级元素，父元素有上外边距同时子元素也有上边距，此时父元素会塌陷较大的外边距值。

![image-20220208103559955](https://gitee.com/lvyehao/assets/raw/master/img/image-20220208103559955.png)

解决方案：

1. 可以给父元素定义上边框`border:1px solid transparent` transparent(透明) 。
2. 可以为父元素定义上内边距`padding:1px`。
3. 可以为父元素添加`overflow:hidden`。

**清除内外边距**

网页元素很多都默认带有内外边距，而且不同的浏览器默认的也不一致。因此我们在布局前，首先要清除下网页元素的内外边距。

```css
/*在网页布局开始时，样式就应该去除边距*/
* {
    padding:0;
    margin:0;
}
```

注意：行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距。但是转换为块级和行内块元素就可以了。

### PS基本操作

因为网页美工大部分效果图都是利用PS(Photoshop)来做的，所以以后我们大部分切图工作都是在PS里面完成。

- Ctrl+R:可以打开标尺，或者视图->标尺。
- 点击标尺，把里面的单位改为像素。
- Ctrl+加号(+)可以放大视图，Ctrl+加号(-)可以缩小视图。
- 按住空格键，鼠标可以变成小手，拖动PS视图。
- Ctrl+D可以取消选区，或者在旁边空白处点击一下取消选区。

案例：小米商品卡片

案例地址：https://yehudah0912.github.io/miuicard.html

案例快照：

![image-20220208141053988](https://gitee.com/lvyehao/assets/raw/master/img/image-20220208141053988.png)

总结：

- 布局中使用不同标签的盒子：标签都是有语义的，合理的地方用合理的标签。比如产品标题就用h,大量文字段落就使用p。
- 多起类名：类名就是给每个盒子起了一个名字，可以更好的找到这个盒子，选取盒子更加的容易，后期也便于维护。

- margin和padding使用的时机：大部分情况下是可以混用的，根据特性和实际情况使用，选取最简单、最便捷的使用方法。

- 去掉无序列表的项目符号，语法:`list-style:none`

  

## 圆角边框

在CSS3中，新增了圆角边框样式，`border-radius`属性用于设置元素的外边框圆角。

语法：

`border-raduis:length;`length:百分比||像素值

`border-raduis:左上 右上 右下 左下;`顺时针方向转。还有两个值的为对角线分，三个值等。

`border-top-left-radius`x4个角的方位依次设置值。

radius半径原理：(椭)园与边框的交集形成圆角效果

![image-20220211172149832](https://gitee.com/lvyehao/assets/raw/master/img/image-20220211172149832.png)

实例：<a href="https://yehudah0912.github.io/radius.html" target="_blank">圆角边框案例示范</a>

```css
div
{
    border:2px solid;
    border-radius:25px;
}
```

小技巧： 

- 参数值可以为数值或者百分比的形式。

- 当盒子元素为正方形的时候，设置`border-radius:50%`就是圆形。
- 如果是一个矩形，设置为高度的一半可以做圆角按钮。
- 该属性是一个简写属性，可以跟四个值，分别代表`左上角、右上角、右下角和左下角`。



## 盒子阴影(常用)

CSS3中新增了盒子阴影，我们可以使用`box-shadow`属性为盒子添加阴影。

语法：`box-shadow:h-shadow v-shadow blur spread color inset`

| 属性值   | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| h-shadow | 必需。水平阴影的位置。允许负值。(x轴距离)                    |
| v-shadow | 必需。垂直阴影的位置。允许负值。(y轴距离)                    |
| blur     | 可选。模糊距离。（可以理解成羽化程度）                       |
| spread   | 可选。阴影的尺寸。(影子的大小)                               |
| color    | 可选。阴影的颜色。请参阅CSS颜色值。(一般结合rgba使用，有透明度看起来更真实。) |
| inset    | 可选。将外部阴影(outset)改为内部阴影。                       |

> 注意: 
>
> 1. 默认的是外阴影(outset)，但是作为默认值不可以写这个单词，否则导致阴影无效。
> 2. 盒子阴影不占用空间，不会影响其他盒子的排列。



## 文字阴影

CSS3中新增了文字阴影，我们可以使用`text-shadow`属性为文字添加阴影。

语法：`text-shadow:h-shadow v-shadow blur color`

| 属性值   | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| h-shadow | 必需。水平阴影的位置。允许负值。(x轴距离)                    |
| v-shadow | 必需。垂直阴影的位置。允许负值。(y轴距离)                    |
| blur     | 可选。模糊距离。（可以理解成羽化程度）                       |
| color    | 可选。阴影的颜色。请参阅CSS颜色值。(一般结合rgba使用，有透明度看起来更真实。) |



## 浮动(float)

### 什么是浮动?

float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

语法：`选择器{float:属性值;}`

| 属性值 | 描述             |
| ------ | ---------------- |
| none   | 元素不浮动(默认) |
| left   | 元素左浮动       |
| right  | 元素有浮动       |

### 浮动特性(重难点)

1. 浮动元素会脱离标准流==(脱标)==。

   > 脱离标准普通流的控制(浮)移动到指定位置(动),（俗称脱标）。
   >
   > 浮动的盒子不再保留原先的位置。

2. 浮动的元素会一行内显示并且元素顶部对齐。

   > 浮动的元素是互相贴靠在一起的(不会有缝隙)，如果==父级元素宽度装不下这些浮动的盒子，多出的盒子就会另起一行对齐==。

3. 浮动的元素会具有行内块元素的特性。

   > 任何元素都可以浮动。不管原先是什么模式的元素，添加浮动之后具有==行内块元素==的相似特性。
   >
   > 如果块级盒子没有设置宽度，默认宽度和父级一样宽，但是添加浮动后，它的大小根据内容来定。

### 浮动元素经常和标准流父级搭配使用

1. 为了约束浮动元素的位置，我们网页布局一般采取的策略是：

2. 先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。符合网页布局第一准则。

浮动案例：<a href="https://yehudah0912.github.io/miuifloat.html" target="_blank">小米商城浮动案例</a>

