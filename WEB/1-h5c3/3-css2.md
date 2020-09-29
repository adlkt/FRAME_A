# css

层叠样式表 (Caacading Style Sheets, 缩写为 CSS) , 是一种样式表语言，用来描述 HTML 文档的呈现。

## css 实例

css 规则由两个注意的部分构成：选择器，以及一条或多条声明。

## css 注释

css 注释以 `/*`开始吗，以`*/`结束

## css 创建

- 内联样式表
- 内部样式表
- 内联样式

## 选择器的继承与优先级

>文字相关的样式可以被继承，布局相关的样式不能被继承（默认是不能被继承的，但是可以设置继承属性的 inherit 值）

1. 相同样式的优先级，后面的优先级比较高
2. 内部样式与外部样式的优先级相同，如果设置了相同样式，后引入的样式优先级高
3. 单一样式的优先级
  `style行内 > id > class > tag >通配* > 继承`
    权重：
    style 行间  1000
    id         100
    class      10
    tag        1
4. !important 提示样式优先级
5. 标签 + 类 大于 单类

## 伪类与伪元素

伪类本质上是为了弥补常规 css 选择器的不足，一边获取到更多信息。通常表示获取不存在与 DOM 树中的信息，或获取不能被常规 css 选择器获取的信息

伪元素本质上是创建了一个右内容的虚拟容器。这个容器不包含任何 DOM 元素，但是可以包含内容。另外，开发者还可以为伪元素定制样式

## 盒子模型的一些问题

1. margin 叠加问题，出现在上下 margin 同时存在的时候。会取较大的作为叠加的值
2. margin 传递问题，出现在嵌套的结构中，只是针对 margin-top 的问题

## BFC

>Block Formatting context（块级格式化上下文）, 具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。

### 触发 BFC

触发 BFC 规范的元素，可以形成一个独立的容器，不受到外界的影响，从而解决一些布局问题。

1. 浮动元素：float 除 none 以外的值
2. 绝对定位元素：position(absolute fixed)
3. display 为 inline-block table-cells,flex
4. overflow 除了 visible 以外的值 (hidden auto scroll)

### BFC 特性及应用

- 解决 margin 叠加问题
- 解决 margin 传递问题
- 解决浮动问题
- 解决覆盖问题

## 精灵图

css 精灵图是一种网页图片的应用处理方式。它允许你将一个页面涉及到的所有的零星图片都包含到一张大图中去加载

好处
  可以减少图片的质量，网页图片的加载速度快
  可以减少图片的请求的次数，加快网页的打开

## 文本省略号

width 必须有一个固定的宽
white-space:nowrap: 不让内容折行
overflow:hidden: 溢出隐藏
text-overflow:ellipsis: 添加省略号

## ## 动画

### transform 变形

- translate: 位移
  translateX
  translateY
  translateZ (3d)

- sacle: 缩放
  scaleX
  scaleY
  scaleZ  (3d)

- rotate: 旋转
  rotateX (3d)
  rotateY (3d)
  rotateZ（和 rotate 是等级关系，正时针按顺时针旋转，负值按逆时针旋转）

- skew: 斜切
  skewX: 单位也是角度，正值向左倾斜，负值向右倾斜
  skewY:

### transform 的注意事项

1. 变形操作不会影响到其他元素
2. 变形操作只能添加给块元素，但是不能添加到内联元素
3. 复合写法，可以同时添加给多个变形操作
    执行是有顺序的，先执行后面的操作，再执行前面的操作
    translate 会受到 rotate ,scale skew 的影响
4. transform-orgin: 基点的位置
    x y z(3d)

### animation 动画

- `animation-name`: 设置动画的名字（自定义的）
- `animation-duration`: 动画的持续时间
- `animation-delay`: 动画的延迟时间
- `animation-iteration-count`: 动画的重复次数，默认值是 1,infinite 无限次数
- `animation-timing-function`: 动画的运动形式

注：
1. 运动结束后，默认情况下会停留在起始位置
2. @keyframes:
    form -> 0% , to -> 100%

### animation 扩展

- `animation-fill-mode`: 规定动画播放之前或之后，其动画效果是否可见。
  none（默认值）: 在运动结束之后回到初始位置，在延迟情况下，让 0% 在延迟后生效
- ` backwards`: 在延迟的情况下，让 0% 在延迟前生效。
- `forwards`: 在运动结束之后，停到结束位置。
  both:bcakwards 和 forwards 同时生效
- `animation-direction`: 属性定义是否应该轮流反向播放动画
  alternate: 一次正向 ( 0% ~ 100% ), 一次方向 ( 100% ~ 0% )
  reverse: 永远都是反向，从 100% ~ 0%
  normal（默认值）: 永远都是正向，从 0% ~ 100%

### animat.css

一款强大的预设 css3 动画库

基本使用：
  animated: 基类（基础的样式，每个动画效果都需要加）
  infinte: 动画的无限次数

### 3D 操作

transform:
  rotateX(): 正值向上翻转
  rotateY(): 正值向右翻转
  translateZ(): 正值向前，负值向后
  scaleZ(): 立体元素的厚度

3d 写法
  scale3d(): 三个值 x y z
  translate3d(): 三个值 x y z
  rotate3d(); 四个值 0|1(x 轴是否添加旋转角度）0|1(y 轴是否添加旋转角度）0|1(z 轴是否添加旋转角度）

`perspective`（景深）: 离屏幕多远的距离去观察元素，值越大幅度越小
`perspective-origin`: 景深 - 基点位置，观察元素的角度
`trnasform-origin`: cnter center -50px (z 轴只能写数值，不能写单词）
`transform-style`:3d 空间
  flat（默认值 2d) preserve-3d( 产生一个三维空间）
`backface-visibility`: 背面隐藏
  hidden,visible（默认值）

## flex

### flex 基本概念

Flex 是 Flexible Box 的缩写，意味"弹性布局", 用来为盒装模型提供最大的灵活性。

在 flex 容器中默认存在两条轴，`水平主轴 (main axis)` 和`垂直的交叉轴 (cross axis)`, 这是默认的设置，当然你可以根据修改使垂直方向变为主轴，水平方向变为交叉轴。

在容器中的每个单元块被称之未 flex item, 每个项目占据的主轴空间为 (main size), 占据的交叉轴的空间为 (cross size)

### flex 容器

```css
.container{display:flex | inline-flex } // 可以有两种取值
```

**需要注意的是：当你设置为 flex 布局之后，子元素的 float,clear,vertical-align 的属性将会失效。**

### flex 容器属性

有下面六种属性可以设置在容器上，它们分别是：
1. flex-direction  决定主轴的排列方向
2. flex-wrap       决定容器内项目是否可换行
3. flex-flow        flex-direction 和 flex-wrap 的简写形式
4. justify-content  定义项目在主轴上的对齐方式
5. align-item       定义项目在交叉轴上的对齐方式
6. align-content    定义了多根轴线的对齐方式

### flex 项目属性

1. order       定义项目在容器中的排列顺序
2. flex-basis  定义分配多余空间之前，项目占据的主轴空间
3. flex-grow   定义项目的放大比例
4. flex-shrink 定义项目的缩小比例
5. flex        flex-grow,flex-shrink 和 flex-basis 的简写
6. align-self  允许单个项目与其他项目不一样的对齐方式

## 移动端

### Viewport 视口

在移动端 viewport 视口就是浏览器显示页面内容的屏幕区域。在 viewport 中有两种视口，分别为 visual viewport （可视视口）和 layout viewport（布局视口）

visual viewport 固定大小跟屏幕大小相同，在上面，而 layout viewport 可改变大小，layout viewport 默认大小为 980 像素，可通过 documnet.documentElement.clientWidth 获取。

现代网页需要将 layout viewport 设置成跟 visual viewport 等同大小，方便进行网页制作。

### viewport 设置

取值|含义
|-|-|
width|设置 layout viewport 的宽度特定值，device-width 表示设备宽
height|设置 layout viewpoet 的高度特定值，一般不进行设置
initial-scale|设置页面的初始缩放
minimun-scale|设置页面的最小缩放
maximum-scale|设置页面的最大缩放
user-scalable|设置页面能否进行缩放

### 移动端适配方案

1. 百分比布局，流式布局
2. 等比缩放布局，rem 布局

#### rem 布局

动态设置 font-size
  通过 JS
  通过 VW
注意：要给 body 重置一下 font-size:16px

```js
const fontSize = document.documentElement.clientWidth / 3.75
document.documentElement.style.fontSize = `${fontSize}px`

// px2rem插件
```

```css
html{font-size:26.66666667vw}
body{font-size:16px}
```

## 媒体查询

常见选项：
  媒体类型
  and not
  min-width max-width
  orientation orientation:landscape

```css
    #box {
      width: 180px;
      height: 100px;
      background-color: red;
    }

    @media screen and (min-width: 500px) and (max-width:700px) {
      #box {
        background: blue
      }
    }
```

## 字体图标

font-face 是 css3 中的一个模块，它主要是把自定义的 web 字体嵌入到网页中

好处
1. 可以非常方便的改变大小和颜色
2. 放大后不会失真
3. 减少请求次数和提交加载速度
4. 简化网页布局
5. 减少工作量
6. 可以使用计算机没有提供的字体

使用
  @font-face 语法
  .woff 等文件都是兼容处理

```css
/* iconfont */

@font-face {
  font-family: "iconfont logo";
  src: url();
  src: url() format('embedded-opentype'),
    url() format('woff'),
    url() format('truetype'),
    url() format('svg');
}
```

## 关键帧动画

## css 新特性

```css
:root {
  --red: red;
}

p {
  color: var(--red);
}
```

## 架构与文件组织

在一个大型项目中，由于页面过多，导致 css 代码难以维护和开发。所以 css 架构可以帮助我们解决文件管理与文件划分等问题。

首先要对 css 进行模块化处理，一个模块负责一类操作行为。可利用 css 预处理器来实现。

文件夹|含义
|-|-|
base|一些初始的通用 css, 如重置默认样式，动画，工具，打印等
components|用于构建页面的所有组件，如按钮，表单，表格，弹窗等
layout|用于布局页面的不同部分，如页眉，页脚，弹性布局，网格布局等
pages|放置页眉之间不同的样式，如首页特殊样式，列表页特殊样式等
themes|应用不同的主题样式时，如管理员，买家，卖家等
abstacts|放置一些如：变量，函数，响应式等辅助开发的部分
vendors|放置一些第三方独立的 css 文件，如 bootstrap,iconfont 等

## postcss

是一个用 JavaScript 工具和插件转换 CSS 代码的工具

## ## grid 网格布局

### 介绍

Grid 布局是一个二维的布局方法，纵横两个方向总是同时存在

作用在 grid 容器上|作用在 grid 子项上
|-|-|
grid-template-columns|grid-column-start
grid-template-rows|grid-column-end
grid-template-areas|grid-row-start
grid-template|grid-row-end
grid-column-gap|grid-row
justify-items|grid-area
align-items|justify-self
place-items|align-self
justify-content|place-self
align-content|
place-content|

### 父容器属性

#### grid-template-columns 和 grid-template-rows

对网格进行横纵划分，形成二维布局。单位可以是像素，百分比，自适应以及 fr 单位（网格剩余空间比例单位）

有时候，我们网格的划分是很有规律的，如果需要添加多个横纵网格时，可以利用 repeat() 语法进行简化操作。

#### grid-template-areas 和 grid-template

area 是区域的意思，grid-template-areas 就是给我们的网络划分区域的。此时 grid 子项只要使用 grid-area 属性指定其隶属于那个区。

grid-template 是 grid-template-rows,grid-template-columns 和 grid-template-area 属性的缩写

#### grid-column-gap 和 grid-row-gap

grid-column-gap 和 grid-row-gap 属性用来定义网格中间隙的尺寸

CSS grid-gap 属性是 grid-column-gap 和 grid-row-gap 属性的缩写

#### justify-items 和 align-items

justify-items 指定了网格元素的水平呈现方式，是水平拉伸显示，还是左中右对齐。align-items 指定了网格元素的垂直呈现方式，是垂直拉伸显示，还是上中下对齐。

place-items 可以让 align-items 和 justify-items 属性写在单个声明中

取值|含含义
|-|-|
stretch|默认值，拉伸。表现伪水平或垂直填充
start|表现为容器左侧或顶部对齐
end|表现为容器右侧或底部对齐
center|表现为水平或垂直居中对齐

#### justify-content 和 align-content

justify-content 指定了网格元素的水平分布方式。align-content 指定了网格元素的垂直分布方式。place-content 可以让 align-content 和 justify-content 属性写在一个 CSS 声明中

取值|含义
|-|-|
stretch|默认值，拉伸。表现为水平或垂直填充
start|表现为容器左侧或顶部对齐
end|表现为容器右侧或底部对齐
center|表现为水平或垂直居中对齐
space-between|表现为两端对齐
space-around|享有独立不重叠的空白空间
space-evenly|平均分配空白空间

### 子项属性

取值|含义
|-|-|
grid-column-start|水平方向上占据的起始位置
grid-column-end|水平方向上占据的结束位置 (span 属性）
grid-row-start|垂直方向上占据的起始位置
grid-row-end|垂直方向上占据的结束位置 (span 属性）
grid-column|grid-column-start + grid-column-end 缩写
grid-row|grid-row-start + grid-row-end 的缩写
grid-area|表示当前网格所占用的区域，名字和位置两种表示方法
justify-self|单个网格元素的水平对齐方式
align-slef|单个网格元素的垂直对齐方式
place-slef|align-slef 和 justify-self 的缩写
