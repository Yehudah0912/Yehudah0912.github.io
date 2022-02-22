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

### 背景颜色

语法：`background-color:颜色值;`

一般情况下元素背景的默认值是`transparent`(透明),我们也可以手动指定背景颜色为透明色。

在CSS3之后加入新的特性：背景半透明`background:rgba();`用于设置==背景颜色的透明状态==。(IE9+版本)

### 背景图片

语法：`background-image:none|url(url)`;

| 参数值 | 作用                           |
| ------ | ------------------------------ |
| none   | 无背景图(默认的)               |
| url    | 使用绝对或相对地址指定背景图像 |

**background-image**属性描述了元素的背景图像。实际开发常见于logo或者一些**装饰性的小图片或者是超大的背景图片**，**优点是非常便于控制位置**。(精灵图也是一种运用场景)

注意：==页面元素既可以添加背景颜色也可以天剑背景图片，只不过背景图片会压住背景颜色。==

### 背景平铺

语法：` background-repeat: repeat|no-repeat|repeat-x|repeat-y`;

| 参数值    | 作用                               |
| --------- | ---------------------------------- |
| repeat    | 背景图像在纵向和横向上平铺(默认的) |
| no-repeat | 背景图像不平铺                     |
| repeat-x  | 背景图像在横向上平铺               |
| repeat-y  | 背景图像在纵向平铺                 |

### 背景图像大小

语法：`background-size: *length*|*percentage*|cover|contain;`；

| 值         | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| length     | 设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为 **auto**(自动) |
| percentage | 将计算相对于背景定位区域的百分比。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
| cover      | 此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。 |
| contain    | 此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小。 |

### 背景图片位置 

语法：`background-position: x y`;

参数代表的是：x坐标和y坐标。可以使用==方位名词==或者是==精确单位==。

| 参数值   | 说明                                              |
| -------- | ------------------------------------------------- |
| length   | 百分数\|有浮点数字和单位标识符组成的长度值        |
| position | top\|center\|bottom\|left\|center\|right 方向名词 |

**参数为方位名词**

- 如果指定的两个值都是方位名词，则两个值的前后顺序无关，比如 left top 和 top left 效果一致。
- 如果指定了一个方位名词，另一个值省略，则第二个值默认居中对齐。

**参数为精确单位**

- 如果参数值是精确坐标，那么第一个肯定是x坐标，第二个一定是y坐标。
- 如果只指定一个数值，那该数值一定是x坐标，另一个默认垂直居中。

**参数是混合单位**

- 如果指定的两个值是精确定位和方位名词混合使用，则第一个值是X坐标，第二个值是Y坐标。

### 背景图像固定(背景附着)

语法：`background-attachment：scroll|fixed`

`background- attachment`属性设置背景图像是否固定或者随着页面的其余部分滚动。

可以用于制作视差滚动效果。

| 参数值 | 说明                               |
| ------ | ---------------------------------- |
| scroll | 背景图像是随对象内容滚动           |
| fixed  | 背景图像固定(不随页面的滚动而滚动) |

背景色半透明：`background：rgba(0,0,0,0.3)`

### 背景复合语法

background：背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置`

案例地址：<a href="https://yehudah0912.github.io/bgc.html" target="_blank">背景透明度案例</a>



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



## 常见网页布局

浮动布局注意点

1. 浮动和标准流的父盒子搭配

   > 先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。

2. 一个元素浮动了，理论上其余的兄弟元素也要浮动。

   > 一个盒子里边有多个盒子，如果其中一个盒子浮动了，那么其他兄弟也应该浮动，避免布局问题。
   >
   > 浮动的盒子只会影响浮动盒子后面的标准流，不会影响前面的标准流。

## 清除浮动

### 思考题

> 我们前面浮动元素有一个标准流的父元素，他们有一个共同的特点，都是由高度的。
>
> 但是，所有的父盒子都必须有高度吗？
>
> 理想状态中的状态，让盒子撑开父亲。有多少孩子元素，我父盒子就有多高。

### 为什么需要清除浮动？

由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子的高度为0时，就会影响下面的标准流盒子。

![image-20220216163139722](https://gitee.com/lvyehao/assets/raw/master/img/image-20220216163139722.png)

由于浮动元素不再占用原文档流的位置，所以它会对后面的元素排版产生影响。

### 清除浮动的本质

- 清除浮动的本质是清除浮动元素造成的影响。
- 如果父盒子本身有高度，则不需要清除浮动。
- 清除浮动之后，父级就会根据浮动的子盒子自动检测高度。父级有了高度，就不会影响下面的标准流了

### 清除浮动

语法：`选择器{clear:属性值};`

| 属性值 | 描述                                     |
| ------ | ---------------------------------------- |
| left   | 不允许左侧有浮动元素(清除左侧浮动的影响) |
| right  | 不允许右侧有浮动元素(清除右侧浮动的影响) |
| both   | 同时清除左右两侧浮动的影响               |

> 我们的实际工作中，几乎只用`clear：both;`
>
> 清除浮动的策略是：闭合浮动。

### 清除浮动的方法

1. **额外标签法**也被称为隔墙法，是W3C推荐的做法。

   > 额外标签法也称为隔墙法，是W3C推荐的做法。
   >
   > 额外标签法会在浮动元素末尾添加一个空的标签。例如`<div class="clear"></div>`，或者其他标签(如`<br/>`等)
   >
   > 优点：通俗易懂，书写方便。
   >
   > 缺点：添加许多无意义的标签，结构化较差。
   >
   > ==注意：要求添加的**空标签**必须是**块级元素**==
   >
   > 案例：<a href="https://yehudah0912.github.io/clearfloat.html" target="_blank">额外标签法实现清除浮动</a>
   >
   > ```html
   > <style>
   > /* 添加清除浮动样式 */
   >   .clear {
   >     clear: both;
   >   }
   > </style>
   > <div class="box">
   >   <div class="ermao">二毛</div>
   >   <!-- 额外标签法 -->
   >   <div class="clear"></div>
   > </div>

2. 父级添加overflow属性。

   > 可以给父级添加`overflow`属性，将其属性值设置为`hidden`、`auto`或`scroll`。
   >
   > ==注意是给父元素添加代码==
   >
   > 优点：代码简洁。
   >
   > 缺点：无法显示溢出部分。
   >
   > 案例：<a href="https://yehudah0912.github.io/clearfloatByOverflow.html" target="_blank">Overflow法实现清除浮动</a>

3. 父级添加:after伪元素。

   > `:after` 方式是额外标签法的升级版。也是给父元素添加。
   >
   > 原理：在父元素后面添加一个容器，使用隔墙法实现。
   >
   > 优点：没有增加标签，结构更简单。
   >
   > 缺点：需要照顾低版本浏览器。
   >
   > 代表网站：百度、淘宝、网易等。
   >
   > 代码：
   >
   > ```html
   > <style>
   > 	/* 固定的样式写法 */
   >   .clearfix:after {
   >     content: '';
   >     display: block;
   >     height: 0;
   >     clear: both;
   >     visibility: hidden;
   >   }
   >   .clearfix {
   >     /* IE6-7兼容IE系列*/
   >     *zoom: 1;
   >   }
   > </style>
   > <body>
   >   <!-- 添加clearfix样式 -->
   >   <div class="box clearfix"></div>
   > </body>
   > ```
   >
   > 案例：<a href="https://yehudah0912.github.io/clearfloatByafter.html" target="_blank">after伪元素法实现清除浮动</a>

4. 父级添加双伪元素。

   > 也是给父元素添加。添加`:before` `:after`伪类元素
   >
   > 原理：在父元素前后都添加一个容器，使用隔墙法实现。
   >
   > 优点：没有增加标签，代码更简洁。结构更简单。
   >
   > 缺点：需要照顾低版本浏览器。
   >
   > 代表网站：小米、腾讯等。
   >
   > 代码：
   >
   > ```html
   >  <style>
   >    .clearfix:before,.clearfix:after {
   >      content: '';
   >      display: table;
   >    }
   >    .clearfix:after {
   >      clear: both;
   >    }
   >    .clearfix {
   >      /* IE6-7兼容IE系列*/
   >      *zoom: 1;
   >    }
   >  </style>
   >  <body>
   >    <!-- 添加clearfix样式 -->
   >    <div class="box clearfix"></div>
   >  </body>
   > ```
   >
   > 案例：<a href="https://yehudah0912.github.io/clearfloatByDoublePseudo.html" target="_blank">双伪元素法实现清除浮动</a>

### 清除浮动总结

1. 父级没有高度。
2. 子盒子浮动了。
3. 影响下面页面标准流的元素布局，需要清除浮动。

| 清除浮动的方式      | 优点               | 缺点                              |
| ------------------- | ------------------ | --------------------------------- |
| 额外标签法(隔墙法)  | 通俗易懂，书写方便 | 添加许多无意义的标签，结构化较差  |
| 父级overflow:hidden | 书写简单           | 溢出隐藏                          |
| 父级after元素       | 结构语义化正确     | 由于 IE6-7不支持:after,兼容性问题 |
| 父级双伪类元素      | 结构语义化正确     | 由于 IE6-7不支持:after,兼容性问题 |

## 学成在线案例

### CSS属性书写顺序(重点)

1. 布局定位属性：display/position/float/clear/visibility/overfllow(建议display第一个写，毕竟关系到模式)
2. 自身属性：width/height/margin/padding/border/background
3. 文本属性：color/font/text-decroation/text-align/vertical-align/white-space/break-word
4. 其他属性(CSS3)：content/cursor/border-radius/box-shadow/text-shadow/background : linear-gradient…

### 页面布局整体思路

为了提高网页制作的效率，布局时通常有以下的整体思路： 
1. 必须确定页面的版心（可视区），我们测量可得知。 
2. 分析页面中的行模块，以及每个行模块中的列模块。即页面布局第一准则。
3. 一行中的列模块经常浮动布局, 先确定每个列的大小,之后确定列的位置。即页面布局第二准则。
4. 制作 HTML 结构。我们还是遵循，先有结构，后有样式的原则。结构永远最重要。
5. 所以, 先理清楚布局结构,再写代码尤为重要。这需要我们多写多积累。

网页布局第一准则：多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动。
网页布局第二准则：先设置盒子大小，之后设置盒子的位置。

### 头部导航制作

在实际开发中，我们不会直接用连接a而是用li+a的做法。

li+a语义更清晰，一看就是有条理的列表型内容。

如果直接用a，搜索引擎容易辨别为有堆砌关键字的嫌疑(故意堆砌关键字容易被搜索引擎降权，有降权风险)从而影响网站排名。

### banner制作

浮动的盒子没有外边距合并问题

## 定位

### 导读：为什么要定位

1. 某个元素可以自由的在一个盒子内移动位置，并且压住其他盒子。

2. 有很多的效果，标准流或浮动都无法快速实现，此时需要定位来实现。

   > - 浮动可以让多个块级盒子一行没有缝隙排列显示，经常用于横向排列盒子。
   > - 定位则是可以让盒子只有的在某个盒子内移动位置或者固定屏幕中的某个位置，并且可以压住其他的盒子。

### 定位组成

定位：将盒子定在某一个位置，所以定位也是在摆放盒子，按照定位的方式移动盒子。

定位 = 定位模式+边偏移

定位模式用于指定一个元素在文档中的定位方式。边偏移则决定了该元素的最终位置。

### 定位模式

定位模式决定元素的定位方式，它通过CSS的position属性来设置，其值可以分为四个：

| 值       | 语义     |
| -------- | -------- |
| static   | 静态定位 |
| ralative | 相对定位 |
| absolute | 绝对定位 |
| fixed    | 固定定位 |

### 边偏移

边偏移就是定位的盒子移动到最终位置。有top bottom left right 4个属性。

| 边偏移属性 | 实例           | 描述                                             |
| ---------- | -------------- | ------------------------------------------------ |
| top        | `top: 80px`    | 顶端偏移量，定义元素相对于其父元素上边线的距离。 |
| bottom     | `bottom: 80px` | 底部偏移量，定义元素相对于其父元素下边线的距离。 |
| left       | `left: 80px`   | 左侧偏移量，定义元素相对于其父元素左边线的距离。 |
| right      | `right: 80px`  | 右侧偏移量，定义元素相对于其父元素右边线的距离。 |

### 静态定位static

静态定位是元素的默认定位方式，无定位的意思。

语法：`选择器 {position：static}`

- 静态定位按照标准流特性摆放位置，它没有偏移量。
- 静态定位在布局时很少用到。

### 相对定位relative(重要)

相对定位是元素在移动位置的时候，是相对它原来的位置来说的(自恋型)。

语法:`选择器 {position：relative;}`

![image-20220218155513556](https://gitee.com/lvyehao/assets/raw/master/img/image-20220218155513556.png)

相对定位的特点：

1. 它是相对于自己原来的位置来移动的(==移动位置的时候参照点是自己原来的位置==)。

2. 原来在标准流的位置继续占有，后面的盒子任然以标准流的方式对待它(==不脱标，继续保留原来的位置==)。

   因此，相对定位并没有脱标。它最典型的应用时给绝对定位当爹的。。。

### 绝对定位absolute(重要)

绝对定位是元素在移动位置的时候，是相对于它祖先元素来说的(拼爹型)。

语法：`选择器{position:absolute;}`

绝对定位的特点：

1. 如果没有祖先元素或者祖先元素没有定位，则以浏览器为准定位(document文档)。
2. 如果祖先元素有定位(相对、绝对、固定定位)，则以==最近一级的有定位祖先元素为参考点移动位置==。
3. 绝对定位不在占有原先的位置(脱标)。

### 子绝父相的由来

子绝父相：自己使用绝对定位，父级则需要相对定位。

弄清楚这个口诀，就明白了绝对定位和相对定位的使用场景。

这个‘子绝父相’太重要了，是我们学习定位的口诀，是定位中最常用的一种方式。

1. 子级绝对定位不会占有位置，可以放到父盒子里面的任何一个地方，不会影响其他的兄弟盒子。
2. 父盒子需要加定位限制子盒子在父盒子中显示。
3. 父盒子布局时，需要占有位置，因此父亲只能是绝对定位。

这就是子绝父相的由来，所以相对定位经常用来作为绝对定位的父级。

总结：==因为父级需要占有位置，因此是相对定位，纸盒子不需要占有位置，则是绝对定位。==

当然，子绝父相不是永远不变的，如果父元素不需要占有位置，子绝父绝也会用到。

### 固定定位fixed(重要)

**固定定位是元素固定于浏览器可视区的位置**。主要使用场景：可以在浏览器页面滚动时元素的位置不会改变。

语法： `选择器{position:fixed};`

固定定位的特点：

1. 以浏览器可视窗口为参照点移动元素。
   - 跟父元素没有任何关系。
   - 不随滚动条滚动。
2. 固定定位不在占有原先的位置。
3. 固定定位也是脱标的，其实固定定位也可以看做是一种特殊的绝对定位。

固定定位小技巧：**固定在版型右侧位置**

> 小算法
>
> 1. 让固定定位的盒子`left：50%`。走到浏览器可视区的一半位置。
> 2. 让固定定位的盒子`margin-left:版心宽度一半的距离`多走版心宽度一半的位置。

![image-20220218180215693](https://gitee.com/lvyehao/assets/raw/master/img/image-20220218180215693.png)





### 粘性定位sticky

粘性定位可以被认为是相对定位和固定定位的混合。Sticky粘性的

语法：`选择器{position：sticky;top:10px}`

粘性定位的特点：

1. 以浏览器的可视窗口为参照点移动元素(固定定位特点)。
2. 粘性定位**占有原先的位置**(相对定位特点)
3. 必须添加top left right bottom其中一个才有效。
4. 跟页面滚动搭配使用。兼容性较差，IE不支持。



### 定位的总结

| 定位模式             | 是否脱标           | 移动位置           | 是否常用     |
| -------------------- | ------------------ | ------------------ | ------------ |
| static静态定位       | 否                 | 不能使用边偏移     | 很少         |
| relative相对定位     | 否(占有位置)       | 相对于自身位置移动 | 常用         |
| ==absolute绝对定位== | ==是(不占有位置)== | ==带有定位的父级== | ==常用==     |
| ==fixed固定定位==    | ==是(不占有位置)== | ==浏览器可视区==   | ==常用==     |
| sticky粘性定位       | 否(占有位置)       | 浏览器可视区       | 当前阶段很少 |

注意：

1. 如果一个盒子既有`left`属性也有`right`属性，则默认会执行`left`属性 同理 `top` `bottom` 会执行 `top`；

### 定位叠放顺序z-index

在使用定位布局时，可能会出现盒子重叠的情况。此时，可以使用z-index来控制盒子的前后次序(z轴)

语法：`选择器{z-index:1;}`

- 数值可以是正整数、负整数或0，默认是auto,值越大，盒子越靠上。
- 如果属性值相同，则按照书写顺序，后来居上。
- 数字后面不能加单位。
- 只有定位的盒子才有z-index属性。

### 绝对定位的盒子居中

加了绝对定位的盒子不能通过`margin：auto`水平居中，但是可以通过以下计算方法实现水平和垂直居中。

1. `left:50%`:让盒子的左侧移动到父级元素的水平中心位置。
2. `margin-left:-100px`让盒子向左移动自身宽度的一半。

### 定位特殊属性

绝对定位和固定定位也和浮动类似。

1. 行内元素添加绝对或者固定定位，可以直接设置高度和宽度。
2. 块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。

### 定位的拓展

**脱标的盒子不会触发外边距塌陷**

浮动元素、绝对定位(固定定位)元素都不会触发外边距合并的问题。

### 绝对定位(固定定位)会完全压住盒子

浮动元素不同，只会压住让下面标准流的盒子，但是不会压住下面标准流盒子里面的文字(图片)，==浮动的元素不会压住下面标准流的文字==。

但绝对定位会压住下面标准流所有的内容。

浮动之所以不会压住文字，因为浮动产生的目的最初是为了做文字环绕效果的。文字会围绕浮动元素。

![image-20220219150332862](https://gitee.com/lvyehao/assets/raw/master/img/image-20220219150332862.png)



## 元素的显示与隐藏

类似网站广告，当我们点击关闭就不见了，但是我们重新刷新页面，会重新出现！

本质：让一个元素在页面中隐藏或者显示出来。

### display属性

display属性用于设置一个元素应如何显示。

- display:none;隐藏对象
- display:block;除了转换为块级元素之外，同时还有显示元素的意思。

display隐藏元素后，不在占有原来的位置。

后面应用及其广泛，搭配JS可以做很多的网页特效。

土豆视频遮罩案例：http://yehudah0912.github.io/tudou.html

### visibility可见性

visibility属性用于指定一个元素应可见还是隐藏。

- visibility:visible;元素可视。
- visibility:hidden;元素隐藏。

visibility隐藏元素后，继续占有原来的位置。

如果隐藏元素想要原来的位置，就用visibility:hidden;

如果隐藏元素不想要原来的位置，就用display:none;

### overflow溢出

overflow属性指定了如果内容溢出一个元素的框(超过其指定高度及宽度)时，会发生什么。

| 属性值  | 描述                                       |
| ------- | ------------------------------------------ |
| visible | 不剪切内容也不添加滚动条                   |
| hidden  | 不显示超过对象尺寸的内容，超出的部分隐藏掉 |
| scroll  | 不管超出内容否，总是会显示滚动条           |
| auto    | 超出自动显示滚动条，不超出不显示滚动条     |

一般情况下，我们都不想让溢出的内容显示出来，因为溢出部分会影响布局。

但是如果有定位的盒子，请慎用overflow:hidden 因为它会隐藏多余的部分。

## 精灵图

### 为什么需要精灵图

一个网页中往往会应用很多小背景图像作为修饰，当网页中的图像过多时，服务器就会频繁地接收和发送请求图片，造成服务器请求压力过大，这将大大降低页面的加载速度。

因此，==为了有效的减少服务器接收和发送请求的次数，提高页面的加载速度，出现了CSS精灵技术==(也称CSS Sprites、CSS雪碧)。

核心原理：将网页中的一些小背景图像整合到一张大图中，这样服务器只需要一次请求就可以了。

### 精灵图(sprites)的使用

使用精灵图核心

1. 精灵技术主要针对于背景图片使用。就是把多个小背景图片整合到一张大图片中。
2. 这个大图片也称为sprites 精灵图 或者 雪碧图。
3. 移动背景图片位置，此时可以使用`background-position`。
4. 移动的距离就是这个目标图片的x和y坐标。注意网页中的坐标有所不同。
5. 因为一般情况下都是往上往左移动，所以数值是负值。(网页中的坐标：x轴邮编走是正值，左边走是负值，y轴同理)
6. 使用精灵图的时候需要精确测量，每个小背景图片的大小和位置。

## 字体图标

字体图标使用场景：主要用于显示网页中通用、常用的一些小图标。

精灵图是有诸多优点的，但是缺点很明显。

1. 图片文件还是比较大的。
2. 图片本身放大和缩小会失真。
3. 一旦图片制作完毕想要更换非常复杂。

此时，有一种技术的出现很好的解决了以上问题，就是字体图片iconfont。

字体图标可以为前端工程师提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。

### 字体图标的优点

- 轻量级：一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求。

- 灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等。

- 兼容性：几乎支持所有浏览器。

  注意：字体图标不能替代精灵技术，只是对工作中图标部分技术的提升和优化。

总结：

- 如果遇到一些结构和样式比较简单的小图标，就用字体图标。
- 如果遇到一些结构和样式复杂一点的小图片就用精灵图。

### **字体图标的下载**

推荐下载网站：

- [icomoon字库](https://icomoon.io/) `https://icomoon.io` 推荐指数：:star::star::star::star::star:

IcoMoon成立于2011年，推出了第一个自定义图标字体生成器，它允许用户选择所需要的图标，是他们成一字型。该字库内容种类繁多，非常全面，唯一的遗憾是国外服务器，打开网速较慢。

- [阿里iconFont字库](https://www.iconfont.cn/)`https://www.iconfont.cn/ `推荐指数：:star::star::star::star::star:

  这个是阿里妈妈M2UX的一个iconfont字体图标库，包含了淘宝图标库和阿里妈妈图标库。可以使用AI制作图标上传生成。重点是，免费！

### 字体文件格式

不同浏览器支持的字体格式是不一样的，字体图标之所以兼容是因为包含了主流浏览器支持的字体文件。

- TureType(.ttf)格式.ttf字体是Windows和Mac的最常见字体，支持这种字体的浏览器有`IE9+、Firefox3.5+、Chrome4+、Safari3+、Opera10+、iOS Mobile、Safari4.2+`
- Web Open Font Format(.woff)格式,是一个开放的TrueType/OpenType的压缩版本，同时也支持元数据包的分离，支持这种字体的浏览器有`IE9+、Firefox3.5+、Chrome6+、Safari3.6+、Opera11.1+`
- Embedded Open Type(.eot)格式，.eot字体是IE专用字体，可以从TrueType创建此格式字体，支持这种字体的浏览器有`IE4+`；
- SVG(.svg)格式，.svg字体是基于SVG字体渲染的一种格式，支持这种字体的浏览器有`Chrome4+、Safari3.1+、Opera10.0+、iOS Mobile Safari3.2+`；
- OpenType(.otf)格式，.otf字体被认为是一种原始的字体格式，其内置在TureType的基础上，支持这种字体的浏览器有`Firefox3.5+、Chrome4.0+、Safari3.1+、Opera10.0+、iOS Mobile、Safari4.2+`；

### 字体图标的引入

在CSS样式中全局声明字体：简单理解把这些字体文件通过CSS引入到我们页面中。

一定要注意文件路径的问题。

```css
@font-face {
  font-family: 'icomoon';
  src: url('fonts/icomoon.eot?dyakgf');
  src: url('fonts/icomoon.eot?dyakgf#iefix') format('embedded-opentype'),
    url('fonts/icomoon.ttf?dyakgf') format('truetype'),
    url('fonts/icomoon.woff?dyakgf') format('woff'),
    url('fonts/icomoon.svg?dyakgf#icomoon') format('svg');
  font-weight: normal;
  font-style: normal;
  font-display: block;
}
```

![image-20220221142303542](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221142303542.png)

### 字体图标的追加



如果工作中，原来的字体图标不够用了，我们需要添加心得字体图标到原来的字体文件中。

把压缩包里面的`selection.json`重新上传，然后选中自己想要的新的图标，重新下载的压缩包，并替换原来的文件即可。

![image-20220221143120552](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221143120552.png)

字体案例：[字体图标的使用](https://yehudah0912.github.io/iconFontTest..html)

## CSS三角

网页中常见一些三角形，使用CSS直接画出来就可以，不必做成图片或者字体图标。

![image-20220221144043366](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221144043366.png)

要点：设置盒子宽高为0，设置边框其余边为透明。

语法： 

```css
.box {
  /* 设置盒子宽高为0px */
  width: 0;
  height: 0;
  /* 解决低版本兼容性 */
  line-height: 0;
  font-size: 0;
  /* 需要那条边为底就，设置其他边为透明色 */
  border-bottom: 100px transparent solid;
  border-left: 100px transparent solid;
  border-right: 100px transparent solid;
  border-top: 100px pink solid;
}
```

效果：

![image-20220221144323628](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221144323628.png)

京东三角对话框案例：[CSS三角案例](https://yehudah0912.github.io/triangle.html)

效果图：

![image-20220221145621255](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221145621255.png)

## CSS用户界面样式

### 什么是界面样式

所谓的界面样式，就是更改一些用户操作样式，以便提高更好的用户体验。

- 更改用户的鼠标样式
- 表单轮廓
- 防止表单域拖拽

### 鼠标样式 cursor

语法：`选择器 {cursor:属性值}`

> /* 关键字值 */
> cursor: pointer;
> cursor: auto;
>
> /* 使用URL，并提供一个关键字值作为备用 */
> cursor: url(hand.cur), pointer;
>
> /* URL和xy的坐标偏移值，最后提供一个关键字值作为备用 */
> cursor:  url(cursor1.png) 4 12, auto;
> cursor:  url(cursor2.png) 2 2, pointer;
>
> /* 全局属性 */
> cursor: inherit;
> cursor: initial;
> cursor: unset;

cursor属性为零个或多个值，它们之间用逗号分隔，最后必填一个关键字值。每个<url>指向一个图像文件。浏览器将尝试加载指定的第一个图像，如果无法加载则返回下一个图像，如果无法加载图像或未指定图像，则使用关键字值代表的指针类型。

每个<url>后面都可选跟一对空格分隔的数字<x><y>表示偏移。它们用来设置指针的热点(即自定义图标的实际点击位置)，位置相对于图标的左上角。

例如，下面的例子使用<url>值指定两个图像，为第二个图像提供<x><y>坐标，如果两个图像都无法加载，则返回`progress`关键字值：

```css
cursor: url(one.svg), url(two.svg) 5 5, progress;
```

| 属性值      | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| *url*       | 需使用的自定义光标的 URL。注释：请在此列表的末端始终定义一种普通的光标，以防没有由 URL 定义的可用光标。 |
| default     | 默认光标（通常是一个箭头）                                   |
| auto        | 默认。浏览器设置的光标。                                     |
| crosshair   | 光标呈现为十字线。                                           |
| pointer     | 光标呈现为指示链接的指针（一只手）                           |
| move        | 此光标指示某对象可被移动。                                   |
| e-resize    | 此光标指示矩形框的边缘可被向右（东）移动。                   |
| ne-resize   | 此光标指示矩形框的边缘可被向上及向右移动（北/东）。          |
| nw-resize   | 此光标指示矩形框的边缘可被向上及向左移动（北/西）。          |
| n-resize    | 此光标指示矩形框的边缘可被向上（北）移动。                   |
| se-resize   | 此光标指示矩形框的边缘可被向下及向右移动（南/东）。          |
| sw-resize   | 此光标指示矩形框的边缘可被向下及向左移动（南/西）。          |
| s-resize    | 此光标指示矩形框的边缘可被向下移动（南）。                   |
| w-resize    | 此光标指示矩形框的边缘可被向左移动（西）。                   |
| text        | 此光标指示文本。                                             |
| wait        | 此光标指示程序正忙（通常是一只表或沙漏）。                   |
| help        | 此光标指示可用的帮助（通常是一个问号或一个气球）。           |
| not-allowed | 禁止                                                         |

| 类型            | CSS值                                                        |                                                              | 描述                                                         |
| :-------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| General         | `auto`                                                       |                                                              | 浏览器根据当前内容决定指针样式 例如当是内容是文字时使用text样式 |
| `default`       | ![default.gif](https://developer.mozilla.org/@api/deki/files/3438/=default.gif) | 默认指针，通常是箭头。                                       |                                                              |
| `none`          |                                                              | 无指针被渲染                                                 |                                                              |
| 链接及状态      | `context-menu`                                               | ![context-menu.png](https://developer.mozilla.org/@api/deki/files/3461/=context-menu.png) | 指针下有可用内容目录。                                       |
| `help`          | ![help.gif](https://developer.mozilla.org/@api/deki/files/3442/=help.gif) | 指示帮助                                                     |                                                              |
| `pointer`       | ![pointer.gif](https://developer.mozilla.org/@api/deki/files/3449/=pointer.gif) | 悬浮于连接上时，通常为手                                     |                                                              |
| `progress`      | ![progress.gif](https://developer.mozilla.org/@api/deki/files/3450/=progress.gif) | 程序后台繁忙，用户仍可交互 (与`wait相反`).                   |                                                              |
| `wait`          | ![wait.gif](https://developer.mozilla.org/@api/deki/files/3457/=wait.gif) | 程序繁忙，用户不可交互 (与`progress相反`).图标一般为沙漏或者表。 |                                                              |
| 选择            | `cell`                                                       | ![cell.gif](https://developer.mozilla.org/@api/deki/files/3434/=cell.gif) | 指示单元格可被选中                                           |
| `crosshair`     | ![crosshair.gif](https://developer.mozilla.org/@api/deki/files/3437/=crosshair.gif) | 交叉指针，通常指示位图中的框选                               |                                                              |
| `text`          | ![text.gif](https://developer.mozilla.org/files/3809/text.gif) | 指示文字可被选中                                             |                                                              |
| `vertical-text` | ![vertical-text.gif](https://developer.mozilla.org/@api/deki/files/3456/=vertical-text.gif) | 指示垂直文字可被选中                                         |                                                              |
| 拖拽            | `alias`                                                      | ![alias.gif](https://developer.mozilla.org/@api/deki/files/3432/=alias.gif) | 复制或快捷方式将要被创建                                     |
| `copy`          | ![copy.gif](https://developer.mozilla.org/@api/deki/files/3436/=copy.gif) | 指示可复制                                                   |                                                              |
| `move`          | ![move.gif](https://developer.mozilla.org/@api/deki/files/3443/=move.gif) | 被悬浮的物体可被移动                                         |                                                              |
| `no-drop`       | ![no-drop.gif](https://developer.mozilla.org/@api/deki/files/3445/=no-drop.gif) | 当前位置不能扔下 [bug 275173](https://bugzilla.mozilla.org/show_bug.cgi?id=275173)Windows或Mac OS X中 "no-drop 与not-allowed相同". |                                                              |
| `not-allowed`   | ![not-allowed.gif](https://developer.mozilla.org/@api/deki/files/3446/=not-allowed.gif) | 不能执行                                                     |                                                              |
| `grab`          | ![grab.gif](https://developer.mozilla.org/@api/deki/files/3440/=grab.gif) | 可抓取译者注:grab和grabbing在比较后期才被支持，见浏览器兼容表 |                                                              |
| `grabbing`      | ![grabbing.gif](https://developer.mozilla.org/@api/deki/files/3441/=grabbing.gif) | 抓取中                                                       |                                                              |
| 重设大小及滚动  | `all-scroll`                                                 | ![all-scroll.gif](https://developer.mozilla.org/@api/deki/files/3433/=all-scroll.gif) | 元素可任意方向滚动 （平移）. [bug 275174](https://bugzilla.mozilla.org/show_bug.cgi?id=275174)Windows中, "*all-scroll* 与 *move相同*". |
| `col-resize`    | ![col-resize.gif](https://developer.mozilla.org/@api/deki/files/3435/=col-resize.gif) | 元素可被重设宽度。通常被渲染为中间有一条竖线分割的左右两个箭头 |                                                              |
| `row-resize`    | ![row-resize.gif](https://developer.mozilla.org/@api/deki/files/3451/=row-resize.gif) | 元素可被重设高度。通常被渲染为中间有一条横线分割的上下两个箭头 |                                                              |
| `n-resize`      | ![Example of a resize towards the top cursor](https://developer.mozilla.org/files/4083/n-resize.gif) | 某条边将被移动。例如元素盒的东南角被移动时`使用se-resize`    |                                                              |
| `e-resize`      | ![Example of a resize towards the right cursor](https://developer.mozilla.org/files/4085/e-resize.gif) |                                                              |                                                              |
| `s-resize`      | ![Example of a resize towards the bottom cursor ](https://developer.mozilla.org/files/4087/s-resize.gif) |                                                              |                                                              |
| `w-resize`      | ![Example of a resize towards the left cursor](https://developer.mozilla.org/files/4089/w-resize.gif) |                                                              |                                                              |
| `ne-resize`     | ![Example of a resize towards the top-right corner cursor](https://developer.mozilla.org/files/4091/ne-resize.gif) |                                                              |                                                              |
| `nw-resize`     | ![Example of a resize towards the top-left corner cursor](https://developer.mozilla.org/files/4093/nw-resize.gif) |                                                              |                                                              |
| `se-resize`     | ![Example of a resize towards the bottom-right corner cursor](https://developer.mozilla.org/files/4097/se-resize.gif) |                                                              |                                                              |
| `sw-resize`     | ![Example of a resize towards the bottom-left corner cursor](https://developer.mozilla.org/files/4095/sw-resize.gif) |                                                              |                                                              |
| `ew-resize`     | ![3-resize.gif](https://developer.mozilla.org/files/3806/3-resize.gif) | 指示双向重新设置大小                                         |                                                              |
| `ns-resize`     | ![6-resize.gif](https://developer.mozilla.org/files/3808/6-resize.gif) |                                                              |                                                              |
| `nesw-resize`   | ![1-resize.gif](https://developer.mozilla.org/files/3805/1-resize.gif) |                                                              |                                                              |
| `nwse-resize`   | ![4-resize.gif](https://developer.mozilla.org/files/3807/4-resize.gif) |                                                              |                                                              |
| 缩放            | `zoom-in`                                                    | ![zoom-in.gif](https://developer.mozilla.org/@api/deki/files/3459/=zoom-in.gif) | 指示可被放大或缩小                                           |
| `zoom-out`      | ![zoom-out.gif](https://developer.mozilla.org/@api/deki/files/3460/=zoom-out.gif) |                                                              |                                                              |



### 取消表单轮廓线outline属性

语法：`outline: none/0`

outline语法

> ```
> /* 样式 */
> outline: solid;
> 
> /* 颜色 | 样式 */
> outline: #f66 dashed;
> 
> /* 样式 | 宽度 */
> outline: inset thick;
> 
> /* 颜色 | 样式 | 宽度 */
> outline: green solid 3px;
> 
> /* 全局值 */
> outline: inherit;
> outline: initial;
> outline: unset;
> ```

**注意：**对于很多元素来说，如果没有设置样式，轮廓是不可见的。因为样式（style）的默认值是 `none`。但 `input` 元素是例外，其样式默认值由浏览器决定。

### 取消拖拽文本域resize属性

语法：`resize:none`

 **`resize`** CSS 属性允许你控制一个元素的可调整大小性。

| 属性值     | 描述                                     |
| ---------- | ---------------------------------------- |
| none       | 元素不能被用户缩放                       |
| both       | 允许用户在水平和垂直方向上调整元素的大小 |
| horizontal | 允许用户在水平方向上调整元素的大小       |
| vertical   | 允许用户在垂直方向上调整元素的大小。     |

**注意：**如果某个元素块的[`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)属性被设置`visible`，则该属性被设置为`resize`无效。

综合案例：https://yehudah0912.github.io/UserInterfaceStyle.html



## vertical-align属性应用

CSS 的属性 **`vertical-align`** 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。

CSS的vertical-align属性的使用场景：经常用于设置图片或者表单(行内块元素)和文字垂直对齐。

官方解释：用于设置一个元素的垂直对齐方式，但是它只针对于行内元素或者行内块元素有效。

![image-20220221163745581](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221163745581.png)

### 图片、表单和文字对齐

图片、表单都属于行内块元素，默认的vertical-align是基线对齐。

此时可以给图片、表单这些行内块元素的vertical-align属性设置为middle就可以让文字和图片垂直居中对齐了。



vertical-align属性可被用于两种环境：

- 使行内元素盒模型与其行内元素容器垂直对齐。例如，用于垂直对齐一行文本内的图片：

  ![image-20220221163444899](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221163444899.png)

- 垂直对齐表格单元内容:

![image-20220221163547187](https://gitee.com/lvyehao/assets/raw/master/img/image-20220221163547187.png)

注意 `vertical-align` 只对==行内元素、行内块元素和表格单元格元素生效==：不能用它垂直对齐块级元素。

语法:

```
/* Keyword values */
vertical-align: baseline;
vertical-align: sub;
vertical-align: super;
vertical-align: text-top;
vertical-align: text-bottom;
vertical-align: middle;
vertical-align: top;
vertical-align: bottom;

/* <length> values */
vertical-align: 10em;
vertical-align: 4px;

/* <percentage> values */
vertical-align: 20%;

/* Global values */
vertical-align: inherit;
vertical-align: initial;
vertical-align: unset;
```

### 解决图片底部默认空白缝隙问题

bug:图片底侧会有一个空白间隙，原因是行内块元素会和文字的基线对齐。

主要解决方法有两种：

1. 给图片添加`vertical-align:middle|top|bottom`等。(提倡使用的)
2. 把图片转换为块级元素`displa：block;`



应用案例 **https://yehudah0912.github.io/vertical-alignTest.html**



## 溢出文字省略号显示

### 单行文本溢出

单行文本溢出显示省略号--必须满足三个条件

```css
.box>p {
  /* 1.先强制一行内显示文本 */
  white-space: nowrap;
  /* 2.超出部分隐藏 */
  overflow: hidden;
  /* 3.文字用省略号代替超出部分 */
  text-overflow: ellipsis;
}
```

### 多行文本溢出

多行文本溢出显示省略号，有较大的兼容性问题，适用于webKit浏览器或移动端(移动端大部分是webKit内核)。

```css
.multiple {
  /* 1.超出部分隐藏 */
  overflow: hidden;
  /* 2.文字用省略号代替超出部分 */
  text-overflow: ellipsis;
  /* 弹性伸缩盒子模型显示 */
  display: -webkit-box;
  /* 限制在一个块元素显示的文本行数 */
  -webkit-line-clamp: 3;
  /* 设置或检索伸缩对象的子元素的排列方式 */
  -webkit-box-orient: vertical;
}
```

完整案例：

















