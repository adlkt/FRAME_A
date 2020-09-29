# scss

css 预处理器定义了一种新的语言，其基本思想是，用一种专门的编程语言。为 css 增加了一些编程的特性，如：变量，语句，函数，继承等概念。将 css 作为目标生成文件，开发者就只要使用这种语言进行 css 的编码工作。

## 注释

单行注释不会被编译
多行注释会被编译

## 变量

使用`$`定义变量

```scss
// 定义变量
$number: 123px;
$key: margin;
$i: 2;
```

## 插值

使用`#{}`使用插值。

```scss
.box#{$i} {
  width: $number;
  height: $number;
  #{$key}: auto;
}
```

## 作用域

Scss 的作用域是有顺序的

```scss
// Sass的作用域是有顺序的
.box3 {
  height: $number;
  $number: 456px;
  width: $number;
}
```

## 选择器嵌套 / 伪类嵌套 / 属性嵌套 (Scss)

```scss
ul {
  list-style: none;
  &:hover {
    color: red;
    // 属性嵌套
    font: {
      size: 10px;
      weight: bold;
      family: "宋体";
    }
  }
  li {
    float: left;
    div {
      margin: 10px;
    }
    p {
      margin: 20px;
    }
  }
}

```

## 运算，单位，转义，颜色

```scss
.box4 {
  $num: 100px;

  width: $num * 3;

  // Sass中如果单位不同的话,是不能运算的
  // height: $num + 20em;
  font: 20px/1.5;

  //  默认 / 是分割的操作
  padding: (20px/1.5);

  color: #010203 * 2;
}
```

## 函数

```scss
@function sum($m, $n) {
  @return $m + $n;
}
.box5 {
  // 内置函数
  width: round(3.4px);
  height: (percentage(0.2));
  margin: random();
  font-size: sum(4px, 5px);
}
```

## 混入

```scss
@mixin show {
  display: block;
}
@mixin hide($color) {
  display: none;
  color: $color;
}

.box6 {
  width: 100px;
  @include show;
  @include hide(red);
}
```

## 继承

```scss
// .line {
//   display: inline;
// }

// 使用百分号不会生成到页面上
%line {
  display: inline;
}

.box7 {
  @extend %line;
}
.box8 {
  @extend %line;
}
```

## 合并，媒体查询

```scss
// 合并
$background: (
  a: url(a.png),
  b: url(b.png),
);
$transform: (
  a: scale(2),
  b: rotate(30deg),
);
.box9 {
  background: map-values($background);
  transform: zip(map-values($transform)...);
}

// 媒体查询
.box10 {
  width: 100px;
  @media screen and (min-width: 768px) {
    width: 600px;
  }
  @media screen and(min-width:1440px) {
    width: 900px;
  }
}
```

## 条件，循环，导入

```scss
// 条件
.box11 {
  $counter: 5;
  @if ($counter >4) {
    width: 100px + $counter;
  } @else {
    width: 10px + $counter;
  }
}

// 循环
@for $i from 0 to 2 {
  .box-#{$i} {
    width: 100px + $i;
  }
}

// 导入

@import "./style.css";
```
