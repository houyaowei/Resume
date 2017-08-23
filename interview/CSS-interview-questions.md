1、什么是CSS reset

```
在不同浏览器之间，默认样式有着诸多差异和问题，而为了在不同浏览器之间具备相同的视觉效果，
开发人员往往会在样式表文件中引入一段CSS代码,
重置库：http://necolas.github.io/normalize.css/，bootstrap也在用这个
```
2、CSS性能优化

```
1.样式放在文档头部，脚本放在文档底部。
2.根据浏览器工作过程，我们知道渲染是在加载完样式文件后开始的，所以样式文件放在头部可减少页面空白的时间，而放在底部，页面需要等待HTML内容加载完成才会加载样式文件，就会导致页面有段时间没有样式
3、减少使用import或者不使用import，压缩文件体积等方式来减少网络请求
4、尽量避免使用： expression表达式以及filter属性。expression表达式在文档的很多交互事件中都会执行，如页面滚动，鼠标滚动等；而filter属性很耗内存,不仅如此，所以用到该filter的元素渲染时都会重新分析该样式，而且下载filter里的图片会导致浏览器停止渲染
5、css缩写：尽量直接对该属性设置多个值，避免多个值分开设置
6、减少使用不必要的并行规则，如button#oneBtn{...},button.btn{...}。对于浏览器来讲，定位一个oneBtn和.btn比同时定位button#oneBtn,button.btn更快
7、尽量减少规则层数，层数越多，定位越慢，一个有语义的选择器往往能够取得更好的效率
8、减少重布局以及重绘

```
3、浏览器工作原理

```
http://www.houyuewei.cn/2015/12/08/how-browser-works-part1/

```
4、link和@import的区别

```
　1、link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS。
　2、link引用CSS时，在页面载入时并行加载；@import需要页面网页完全载入以后加载。
　3、link是XHTML标签，无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持。
　4、ink支持使用JavaScript控制DOM去改变样式；而@import不支持。
```
5、css中可继承和不可继承的属性

```
1、不能继承的属性
 1）display 
 2)文本属性：vertical-align,text-decoration,text-shadow,white-space
 3)盒子模型属性：width,height,margin,border,border-color,border-image,padding
 4)背景属性
 5）定位属性：float,clear,postion,top-right-bottom-left,min-width,max-width,min-height,max-height,overflow,clip,z-index
 6)内容属性：content
 7)outline属性：outline-style,outline-width,outline-color

2、可继承的属性
 1）字体
 2）文本部分属性：text-indent,text-align,line-height,word-spacing,letter-spacing,text-transform,color
 3)元素可见性：visibility
 4)表格布局：caption-side,border-collapse,border-spacing,可以通过把div设置display:table设置为类table，参考https://developer.mozilla.org/zh-CN/docs/Web/CSS/display
 5）列表布局属性：list-style
  
```
5、CSS预处理

```
CSS预处理是一种技术，可以很好的提升CSS的编程性，开发效率以及可维护性，就是像编写其他程序一样，可以
通过定义变量，调用函数等方式编写程序，最后通过特殊的处理器输出CSS代码。
```
6、浮动的原理和工作方式，会产生什么影响呢，要怎么处理？

```
工作方式：浮动元素脱离文档流，不占据空间。浮动元素碰到包含它的边框或者浮动元素的边框停留。

影响：
1)浮动会导致父元素无法被撑开，影响与父元素同级的元素。
2)与该浮动元素同级的非浮动元素，如果是块级元素，会移动到该元素下方，而块级元素内部的行内元素会环绕浮动元素；而如果是内联元素则会环绕该浮动元素。
3)与该元素同级的浮动元素，对于同一方向的浮动元素(同级)，两个元素将会跟在碰到的浮动元素后；而对于不同方向的浮动元素，在宽度足够时，将分别浮动向不同方向，在宽度不同是将导致一方换行。
4）浮动元素将被视作为块元素
5）要浮动一个非替换元素，则必须为该元素声明一个width。否则，根据CSS规范，元素的宽度趋于0

清除浮动：
1)clear:both
2)给浮动元素添加overflow:auto
```
7、块级元素、行内元素和可变元素

```
块级元素：div，dl,fieldset,form,h1-h6,hr,ol,ul,p,table,pre,center, blockquote
行内元素：a,abbr,br,cite,code,em,font,img,input,label,span, textarea,select
可变元素：applet，button，del, iframe,map
```
8、元素选择器

```
基本选择器：通配符选择器，元素选择器，id选择器，类选择器，群组选择器(selector1,selector2)
层次选择器：
1）后代选择器: E F 选择所有的后代元素，无论有多少层
2）子选择器：E > F 只选择E中的子元素
3）相邻兄弟选择器： E+F ，只选择一个
4)通用兄弟选择器：E ~ F,选择所有的兄弟选择元素
伪类选择器：：link,:visited,:hover,:active
```