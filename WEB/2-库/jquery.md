# jquery

## jquery 选择器

- 基本
  `#id`
  element
  class
  *
  selector1,selector2,selector 将每一个选择器匹配到的元素合并后一起返回
- 层级
  m n
  m > n
  m + n
  m ~ n
- 基本筛选器
  :first
  :not(selector)
  :even
  :odd
  :eq(index) 匹配一个给定索引值的元素
  :gt(index) 匹配所有大于给定索引值的元素
  :lt(index) 匹配所有小于给定索引值的元素
  :last
  :header 匹配如 h1, h2, h3 之类的标题元素
  :animated 匹配所有正在执行动画效果的元素
  :focus
  :root
  :target 选择由文档 URI 的格式化识别码表示的目标元素。
- 内容
  :contains(text) 匹配包含给定文本的元素
  :empty
  :has(selector) 匹配含有选择器所匹配的元素的元素
  :parent 匹配含有子元素或者文本的元素
- 可见性
  :hidden
  :visible
- 属性
  [attribute]
  [attribute=value]
  [attribute!=value]
  [attribute^=value]
  [attribute$=value]
  [attribute*=value]
  `[attrSel1][attrSel2][attrSelN]`
- 子元素
  :first-child
  :first-of-type
  :last-child
  :last-of-type
  :nth-child
  :nth-last-child()
  :nth-of-type()
  :only:child
  :only-of-type
- 表单
  :input
  :text
  :password
  :radio
  :checkbox
  :submit
  :image
  :reset
  :button
  :file
- 表单对象属性
  :enabled
  :disabled
  :checked
  :selected
- 混淆选择器
  $.escapeSelector(selector)
  这个方法通常被用在类选择器或者 ID 选择器中包含一些 CSS 特殊字符的时候，这个方法基本上与 CSS 中 CSS.escape() 方法类似，唯一的区别是 jquery 中的这个方法支持所有浏览器。

## 文档处理

- 内部插入
  append()
  appendTo()
  prepend()
  prependTo()
- 外部插入
  after()
  before()
  insertAfter()
  insertBefore()
- 包裹
  wrap()
  unwrap()
  wrapAll()
  wrapinner()
- 替换
  replaceWith()
  replaceAll()
- 删除
  empty()
  remove()
  detach()
- 复制
  clone()

## CSS

- css
  css()
  jQuery.csshooks
- 位置
  offset()
  position()
  scrollTop()
  scrollLeft()
- 尺寸
  width()
  height()
  innerWidth()
  innerHeight()
  outerWidth()
  outerHeight()

## 事件

- 页面载入
  ready()
- 事件处理
  on()
  off()
  bind()
  unbind()
  one()
  trigger()
  triggerHandler()
- 事件委派
  live()
  die()
  delegate()
  undelegate()
- 事件切换
  hover()
  toggle()
- 事件
  blur()
  change()
  click()
  dbclick()
  error()
  focus()
  focusin()
  focusout()
  keydown()
  keypreess()
  keyup()
  mousedown([[data],fn])
  mouseenter([[data],fn])
  mouseleave([[data],fn])
  mousemove([[data],fn])
  mouseout([[data],fn])
  mouseup([[data],fn])
  resize()
  scroll()
  select()
  submit()
  unload()

## 事件对象

eve.currentTarget 在事件冒泡阶段中的当前 DOM 元素
eve.data
eve.delegateTarget
eve.isDefaultPrevented()
eve.isImmediatePropag()
eve.isImmediatePropagationStopped()
eve.namespace
eve.pageX
eve.pageY
eve.preventDefault()
eve.relatedTarget()
eve.result
eve.stopImmediatePro()
eve.stopPropagation()
eve.target
eve.timeStamp
eve.type
eve.which

## 属性

- 属性
  attr()
  removeAttr()
  prop()
  removeProp()
- css 类
  addClass()
  removeClass()
  toggleClass()
- html 代码 / 文本 / 值
  html()
  text()
  val()

## 动画

- 基本
  show()
  hide()
  toggle()
- 滑动
  slideDown()
  slideUp()
  slideToggle()
- 淡入淡出
  fadeIn()
  fadeOut()
  fadeTo()
  fadeToggle()
- 自定义
  animate()
  stop()
  delay()
  finish()
- 设置
  jQuery.fx.off
  jQuery.fx.interval

## ajax

- ajax 请求
  $.ajax
  $.get
  $.getJSON
  $.getScript
- ajax 事件
  ajaxComplete()
  ajaxError()
  ajaxSend()
  ajaxStart()
  ajaxStop()
  ajaxSuccess()
- 其他
  load()
  $.ajaxPrefilter([type],fn)
  $.ajaxSetup([options])
  serialize()
  serializeArray()

## 核心

- jQuery 核心函数
  jQuery([sel,[context]])
  jQuery(html,[ownerDoc])
  jQuery(callback)
  jQuery.holdReady(hold)
  jQuery.readyException( error )
- jQuery 对象访问
  each(callback)
  size()
  length
  selector
  context
  get([index])
  index()
- 数据缓存
  data()
  removeData()
  $.data()
- 队列控制
  queue()
  dequeue()
  clearQueue()
- 插件机制
  jQuery.fn.extend()
  jQuery.extend()
- 多库共存
  jQuery.noConflict()

## 延迟对象

def.done(d,[d])
def.fail(failCallbacks)
def.isRejected()1.7-
def.isResolved()1.7-
def.reject(args)
def.rejectWith(c,[a])
def.resolve(args)
def.resolveWith(c,[a])
def.then(d[,f](,p))1.8*
def.promise([ty],[ta])
def.pipe([d],[f],[p])1.8-
def.always(al,[al])
def.notify(args)1.7+
def.notifyWith(c,[a])1.7+
def.progress(proCal)1.7+
def.state()

## 工具

- 浏览器及特性检测
  $.support()
  $.browser()
  $.brower.version()
  $.boxModel()
- 数组和对象操作
  $.each()
  $.extend()
  $.grep()
  $.sub()
  $.when()
  $.makeArray()
  $.map()
  $.inArray()
  $.toArray()
  $.merge()
  $.unique()
  $.uniqueSort()
  $.parseJSON()
  $.parseXML()
- 函数操作
  $.noop
  $.proxy()
- 测试操作
  $.contains()
  $.type()
  $.isArray()
  $.isFunction()
  $.isEmptyObject()
  $.isPlainObject()
  $.isWindow()
  $.isNumeric()
- 字符串操作
  $.trim()
- URL
  $.param()
- 插件编写
  $.error()
  $.fn.jQuery

## 筛选

- 过滤
  eq()
  first()
  last()
  hasClass()
  filter()
  is()
  map()
  has()
  not()
  slice()
- 查找
  children()
  closeet()
  find()
  next()
  nextAll()
  nextAll([expr])
  nextUntil([e|e](,f))
  offsetParent()
  parent([expr])
  parents([expr])
  parentsUntil([e|e](,f))
  prev([expr])
  prevAll([expr])
  prevUntil([e|e](,f))
  siblings([expr])
- 串联
  add()
  andSelf()
  addBack()
  contents()
  end()

## 回调函数

cal.add(callbacks)1.7+
cal.disable()1.7+
cal.empty()1.7+
cal.fire(arguments)1.7+
cal.fired()1.7+
cal.fireWith([c] [,a])1.7+
cal.has(callback)1.7+
cal.lock()1.7+
cal.locked()1.7+
cal.remove(callbacks)1.7+
$.callbacks(flags)1.7+
