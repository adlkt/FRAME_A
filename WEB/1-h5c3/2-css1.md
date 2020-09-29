# 层叠样式表

## 选择器

- ID 选择器 (#)
- 类选择器 (.)
- 标签选择器 (E)
- 群组选择器 (E,F)
- 通配选择器 (*)

- 层次选择器
  后代 (e f)
  父子 (e > f)
  相邻 (e + f)
  兄弟 (e ~ f)

- 属性选择器
  E[attr]
  E[attr='val'] 完全匹配
  E[attr^='val'] 起始匹配
  E[attr$='val'] 结束匹配
  E[attr*='val'] 部分匹配
  E[][][] 组合匹配

- 伪类选择器
- E:link
- E:visited
- E:hover
- E:active

- E:not(s)
- E:root
- E:first-child
- E:last-child
- E:only-child 匹配父元素仅有的一个子元素 E。
- E:nth-child(n)
- E:nth-last-child(n)
- E:first-of-type
- E:last-of-type
- E:only-of-type
- E:nth-of-type(n)
- E:nth-last-of-type(n)

- E:empty
- E:focus
- E:checked
- E:enabled
- E:disabled

- 伪元素选择符
- ::first-letter
- ::first-line
- ::before
- ::after
- ::placeholder
- ::selection

## 浮动与定位

- float
- clear
- visiblity

- position
- top/right/bottom/left
- z-index

- display

## 背景与颜色

- background 简写属性
- background-color 背景颜色
- background-image 背景图片
- background-repeat 背景是否重复及如何重复
- background-attachment 背景图像是否随固定或者随页面其余部分滚动
- background-position  设置背景图像的位置
- background-origin  设置计算背景图片时的参考原点
- background-clip   指定背景图像的裁切部分
- background-size  设置背景图像的大小。

- color
- opacity 透明度
- rgba()

<!-- - hsla() -->

- transparent 透明色

<!-- - currentcolor  是 color 属性的值， -->

## 文本与字体

- font 简写属性
- font-style
- font-variant
- font-weight
- font-size
- font-family

<!-- - font-stretch -->

<!-- - font-size-adjust -->

- text-transform
- white-spacing

<!-- - tab-size -->

- word-break
- word-wrap
- overflow-wrap
- text-align

<!-- - text-align-last -->

<!-- - test-justify -->

- word-spacing
- letter-spacing
- text-ident
- vertical-align
- line-height

<!-- text-size-adjust -->

## 文本与书写

- text-decoration
- text-decoration-line
- text-decoration-color
- text-decoration-style

<!-- - text-decoration-skip -->

- text-shadow

- direction
- unicode-bidi
- writing-mode

## 盒模型，尺寸和补白

- box-sizing

- width
- min-width
- max-width
- height
- min-height
- max-height

- margin
- margin-top
- margin-right
- margin-bottom
- margin-left

- padding
- padding-top
- padding-right
- padding-bottom
- padding-left

## 边框

- border
- border-width
- border-style
- border-color
- border-top/right/bottom/left
- border-radius
- box-shadow
- border-image
- border-image-source
- border-image-slice
- border-image-width
- border-image-outset
- border-image-repeat

## 单位

- px
- em
- rem
- vw
- vh
- %

## 图像

- image()
- image-set

- linear-gradient()
- repeat-linear-gradient()
- radial-gradient()
- repeating-radial-gradient()

## 列表和表格

- list-style
- list-style-image
- list-style-position
- list-style-type

- table-layout
- table-collspase
- border-spacing
- caption-side
- empty-cells

- content
- content-increment
- counter-reset
- quotes

## 过渡，变换，动画

- transition
- transition-property 规定设置过渡效果的 css 属性的名称
- transition-duration 规定完成过渡效果需要多少秒或毫秒
- transition-timing-function 定义过渡效果何时开始（延迟，也可以提前）
- transition-delay 规定过渡效果的速度曲线

- transform
- transform-origin
- transform-style
- perspective
- perspective-origin
- backface-visibility

- animation
- animation-name
- animation-duration
- animation-timing-function
- animation-delay
- animation-iteration-count
- animation-direction
- animation-play-state
- animation-fill-mode

## 用户界面

- appearance
- text-overflow
- outline
- outline-width
- outline-color
- outline-style
- outline-offset
- cursor

<!-- - zoom -->

- box-sizing
- resize
- user-select
- pointer-events

## 函数

- calc()
- filter()

- counter()
- counters()
- attr()

## 语法与规则

- !important
- @import
- @charset
- @media  媒体查询
- @font-face 字体图标
- @keyframes 关键帧
- @supports

## 杂项

- CSSHACK
  条件 Hack
  属性级 Hack
  选择器级 Hack

## 浏览器属性

IE
--Webkit

## 多列

- columns
- column-width 分栏的宽度
- column-count 分栏的个数
- column-gap 分栏的间距
- column-rule 分栏的边线
- column-rule-width
- column-rule-style
- column-rule-color
- column-span 合并分栏
- column-fill 指定如何填充列
- column-break-before
- column0break-after
- column-break-inside

注意：column-width 和 column-count 不要一起去设置。
