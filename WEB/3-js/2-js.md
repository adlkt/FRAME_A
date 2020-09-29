# JavaScript

## DOM

### 概述

`DOM` 是 JavaScript 操作网页的接口，全称为"文档对象模型". 它的作用是将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作。浏览器会根据 DOM 模型，将结构化文档解析成一系列的阶段，再由这些节点组成一个树状结构，所有的节点和最终的树状结构，都有规范的对外接口。

DOM 的最小组成单位叫做`节点`。文档的树形，就是由各种不用类型的节点组成。每个节点可以看作是文档树的一片叶子。节点的类型有七种。`Document`,`DocumentType`,`Element`,`Attr`,`Text`,`Comment`,`DocumentFragment` 浏览器提供了一个原生的节点对象`Node`, 上面七种节点都继承了`Node`, 因此具有一些共同的属性和方法。

一个文档的所有节点，按照所在的层级，可以抽象成一种树状结构。这种树状结构就是 `DOM 树`。它有一个顶层节点，下一层都是顶层的子节点，然后子节点又有自己的子节点，这样层层衍生出一个金字塔结构，又像一棵树。浏览器原生提供`document`节点，代表整个文档。文档的第一层有两个几点，第一个是文档类型节点 (`<!doctype html>`), 第二个是 HTML 网页的顶层容器标签`<html>`, 后者构成了树结构的根节点，其他 html 标签节点都是它的下级节点。除了根节点，其他节点都有三种层级关系。父节点关系，子节点关系，同级节点关系。DOM 提供操作接口，用来获取这三种关系的节点，比如子节点接口包括`firstChild`和`lastChild`等属性，同级节点包括`nextSibling`和`previousSIbling`属性。

### Node 接口

所有 DOM 节点对象都继承了 Node 接口，拥有一些共同的属性和方法。这就是 DOM 操作的基础。

1. `Node.prototype.nodeType`属性返回一个整数值，表示节点的类型
2. `Node.prototype.nodeName`属性返回节点的名称
3. `Node.prototype.nodeValue`属性返回一个字符串，表示当前节点本身的文本值，该属性可读写。
4. `Node.prototype.textContent`属性返回当前节点和它的所有后代节点的文本内容。
5. `Node.prototype.baseURI`属性返回一个字符粗，表示当前网页的绝对路径。
6. `Node.prototype.ownerDocument`属性返回当前节点所在的顶层文档对象，即`document`对象。
7. `Node.prototype.nextSibling`属性返回紧跟再当前节点后面的第一个同级节点。如果当前节点后面没有同级节点，则返回`null`
8. `Node.prototype.previousSibing`属性返回当前节点前面的，距离最近的一个同级节点，如果当前节点前面没有同级节点，则返回`null`. 注意，该属性还包括文本节点和注释节点。因此如果当前节点前面有空格，该属性会返回一个文本节点，内容为空格。
9. `Node.prototype.parentElement`属性返回当前节点的父元素节点，如果当前节点没有父节点，或者父节点类型不是元素节点，则返回`null`
10. `Node.prototype.firstChild`属性返回当前节点的第一个子节点，如果当前节点没有子节点，则返回`null`, 注意，`firstChild`返回的除了元素节点，还可能使文本节点或注释节点，`Node.prototype.lastChild`属性返回当前节点的最后一个子节点，如果当前节点没有子节点，则返回`null`. 用法于`firstCHild`属性相同。
11. `Node.prototype.childNodes`属性返回一个类似数组的对象，成员包括当前几点的所有子节点
12. `Node.prototype.isConnected`属性返回一个布尔值，表示当前节点是否再文档之中。

1. `Node.prototype.appendChild()`方法接受一个节点对象作为参数，将起作为最后一个子节点，插入当前节点，该方法的返回值就是插入文档的子节点。
2. `Node.prototype.hasChildNodes()`方法返回一个布尔值，表示当前节点是否有子节点。
3. `Node.prototype.cloneNode()`方法用于克隆一个节点。它接受一个布尔值作为参数，表示是否同时克隆子节点。它的返回值是一个克隆出来的新节点。
4. `Node.prototype.insertBefore()`方法用于将某个节点插入父节点内部的指定位置。
5. `Node.prototype.removeChild()`方法接受一个子节点作为参数，用于从当前节点移除该子节点。返回值是移除的子节点。如果参数节点不是当前节点的子节点，`removeChild` 方法将报错。
6. `Node.prototype.replaceChild()`方法用于将一个新的节点，替换当前节点的某一个子节点。
7. `Node.prototype.contains()`方法返回一个布尔值，表示参数节点是否满足以下三个条件之一。参数节点为当前节点，参数节点为当前节点的子节点，参数节点为当前节点的后代节点。
8. `Node.prototype.compareDocumentPosition()`方法的用法，与`contains`方法完全一致，返回一个六个比特位的二进制值，表示参数节点对当前节点的关系。
9. `Node.prototype.isEqualNode()`方法返回一个布尔值，用于检查两个节点是否相等。所谓相等的节点，指的是两个节点的类型相同，属性相同，子节点相同。`Node.prototype.isSameNode()`方法返回一个布尔值，表示两个节点是否为同一个节点。
10. `Node.prototype.normalize()`方法用于清理当前节点内部的所有文本节点。它会去除空的文本节点，并且将毗邻的文本节点合并成一个，也就是说不存在空的文本节点，以及毗邻的文本节点。
11. `Node.prototype.getRootNode()`方法返回当前节点所在文档的根节点`document`, 与`ownerDocument`属性的作用相同。

### NodeList 接口，HTMLCollection 接口

节点都是单个对象，有时需要一种数据结构，能够容纳多个节点。DOM 提供两种节点集合，用于容纳多个节点：`NodeList`和`HTMLCollection`. 这两种集合都属于接口规范。许多 DOM 属性和方法，返回的结果是`NodeList`实例或`HTMLCollection`实例。主要区别是，`NodeList`可以包含多种类型的节点，`HTMLCollection`只能包含 HTML 元素节点。

`NodeList`实例是一个类似数组的对象，它的成员是节点对象。通过以下方法可以得到`NodeList`实例。`Node.childNodes`,`document.querySelectorAll()`等节点搜索方法。`NodeList`实例很像数组，可以使用`length`属性和`forEach`方法。但是，它不是数组，不能使用`pop`或`push`之类数组特有的方法。注意，NodeList 实例可能是动态集合，也可能是静态集合。所谓动态集合就是一个活的集合，DOM 删除或新增一个相关节点，都会立刻反映在 NodeList 实例。目前，只有`Node.childNodes`返回的是一个动态集合，其他的 NodeList 都是静态集合。

2. `NodeList.prototype.length`属性返回 NodeList 实例包含的节点数量。
3. `NodeList.prototype.forEach()`
4. `NodeList.prototype.item()`方法接受一个整数值作为参数，表示成员的位置，返回该位置上的成员。
5. `NodeList.prototype.keys()`,`NodeList.prototype.values()`,`NodeList.prototype.entries()`这三个方法都返回一个 ES6 的遍历器对象，可以通过`for...of`循环遍历获取每一个成员的信息。

`HTMLCollection`是一个节点的对象的集合，只能包含元素节点，不能包含其他类型的节点。它的返回值是一个类似数组的对象，但是与`NodeList`接口不同，`HTMLCollection`没有`forEach`方法，只能使用`for`循环遍历。返回`HTMLCollection`实例的，主要是一些`Document`对象的集合属性，比如`document.links`,`document.forms`,`document.iamges`等。`HTMLCollection`实例都是动态集合，节点的变化会实时反映在集合中。如果元素节点有`id`或`name`属性，那么`HTMLCollection`实例上面，可以使用`id`属性或`name`属性引用该节点元素。如果没有对应的节点，则返回`null`

2. `HTMLCollection.prototype.length`属性返回`HTMLCollection`实例包含的成员数量
3. `HTMLCollection.prototype.item()`方法接受一个整数值作为参数，表示成员的位置，返回该位置上的成员。
4. `HTMLCollection.prototype.namedItem()`方法的参数是一个字符串，表示`id`或 `name`属性的值，返回对应的元素节点。如果没有对应的节点，则返回`null`

### ParentNode 接口，ChildNode 接口

节点对象除了继承 Node 接口以外，还拥有其他接口。`ParentNode`接口表示当前节点是一个父节点，提供一些处理子节点的方法。`ChildNode`接口表示当前节点是一个子节点，提供一些相关方法。

如果当前节点是父节点，就会混入了`ParentNode`接口。由于只有元素节点，文档节点和文档片段节点拥有子节点，因此只有这三类节点会拥有`ParentNode`接口。

1. `ParnetNode.children`属性返回一个`HTMLCollection`实例，成员是当前节点的所有元素子节点。该属性只读。
2. `ParentNode.firstElementChild`属性返回当前节点的第一个元素子节点。如果没有任何元素子节点，则返回`null`
3. `ParentNode.lastElementChild`属性返回当前节点的最后一个元素子节点，如果不存在任何元素子节点，则返回`null`
4. `ParentNode.childElementCount`属性返回一个整数，表示当前节点所有元素子节点的数目。如果不包含任何元素子节点，则返回`0`
5. `ParentNode.append()`方法为当前节点追加一个或多个子节点，位置是最后一个元素子节点的后面。该方法不仅可以添加元素子节点，还可以添加文本子节点。主要，该方法没有返回值。`ParentNode.prepend()`方法为当前节点追加一个或多个子节点，位置是第一个元素子节点的前面，它的用法与`append`方法完全一致，也是没有返回值。

如果一个节点有父节点，那么该节点就拥有了`ChildNode`接口。

1. `ChildNode.remove()`方法用于从父节点移除当前节点。
2. `ChildNode.before()`方法用于当前节点前面，插入一个或多个同级节点，两种拥有相同的父节点，注意，该方法不仅可以插入元素节点，还可以插入文本节点`ChildNode.after()`方法用于在当前节点的后面，插入一个或多个同级节点，两种拥有相同的父节点。用法与`before`方法完全一致。
3. `ChildNode.replaceWith()`方法使用参数节点，替换当前节点。参数可以是元素节点，也可以是文本节点。

### Document 节点

`document`节点对象代表整个文档，每张网页都有自己的`document`对象。`window.document`属性就指向这个对象。只要浏览器开始载入 HTML 文档，该对象就存在了，可以直接使用。`document`对象有不同的办法可以获取。1. 正常的网页，直接使用`document`或`window.document`. 2.`iframe`框架里面的网页，使用`iframe`节点的`contentDocument`属性。3.Ajax 操作返回的文档，使用`XMLHttpRequest`对象的`responseXML`属性。4. 内部节点的`ownerDocument`属性。

`document`对象继承了`EventTarget`接口和`Node`接口，并且混入 (mixin) 了`ParentNode`接口。这意味着，这些接口的方法都可以在`document`对象上调用。除此之外，`document`对象还有很多自己的属性和方法。

快捷方式属性：以下属性是指向文档内部的某个节点的快捷方式。
1. `document.defaultView`属性返回`document`对象所属的`window`对象。如果当前文档不属于`window`对象，该属性返回`null`
2. `document.doctype`对于文档来说，`document`对象一般有两个子节点。第一个子节点是`document.doctype`,指向

## BOM

## 事件

## 浏览器模型

## 网页元素接口

## WebApi
