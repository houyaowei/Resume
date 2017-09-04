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
5）伪类选择器：：link,:visited,:hover,:active
6）属性选择器：a[rel = "external"]
7）通配符选择器：*
结构伪类选择器: E:first-child,E:nth-child(n), E:nth-of-type(n)
```
9、对行内元素设置margin-top 和margin-bottom是否起作用

```
不起作用。（需要注意行内元素的替换元素img、input，他们是行内元素，但是可以为其设置宽高，并且margin属性也是对其起作用的，有着类似于Inline-block的行为）
```
10、对内联元素设置padding-top和padding-bottom是否会增加它的高度

```
不会。同上题，要注意行内元素的替换元素，img设置padding-top/bottom是会起作用的
```
11、媒体查询中only的作用

```
only 用来定某种特定的媒体类型，可以用来排除不支持媒体查询的浏览器。其实only很多时候是用来对那些不支持Media Query 但却支持Media Type 的设备隐藏样式表的。其主要有：支持媒体特性（Media Queries）的设备，正常调用样式，此时就当only 不存在；对于不支持媒体特性(Media Queries)但又支持媒体类型(Media Type)的设备，这样就会不读了样式，因为其先读only 而不是screen；另外不支持Media Qqueries 的浏览器，不论是否支持only，样式都不会被采用
```

12、格式化上下文

```
一个块格式化上下文（block formatting context） 是Web页面的可视化CSS渲染出的一部分。它是块级盒布局出现的区域，也是浮动层元素进行交互的区域.
一个块格式化上下文由以下之一创建:
根元素或其它包含它的元素
1)浮动元素 (元素的 float 不是 none)
2)绝对定位元素 (元素具有 position 为 absolute 或 fixed)
3)内联块 (元素具有 display: inline-block)
4)表格单元格 (元素具有 display: table-cell，HTML表格单元格默认属性)
5)表格标题 (元素具有 display: table-caption, HTML表格标题默认属性)
6)具有overflow 且值不是 visible 的块元素，
7)display: flow-root
8)column-span: all 应当总是会创建一个新的格式化上下文，即便具有 column-span: all 的元素并不被包裹在一个多列容器中。
```
13、display:none 和visibilty:hidden的区别

```
两者都是将某个元素隐藏起来，区别是：display:none会使对象彻底消失，不占据空间；但是visibility:hidden所占的空间还在，留了一块空白区域
```
14、XML和JSON的区别
    m
```
1)体积方面：JSON相对于XML来讲，数据的体积小，传递的速度更快些。
2)交互方面：JSON与JavaScript的交互更加方便，更容易解析处理，更好的数据交互。
3)描述方面：JSON对数据的描述性比XML较差。
4)速度方面：JSON的速度要远远快于XML
```
15、介绍一下标准的CSS的盒子模型？和低版本IE的盒子模型有什么不同？

```
标准 w3c 盒子模型的范围包括 margin、border、padding、content，并且 content 部分不包含其他部分。
IE盒子模型的范围也包括 margin、border、padding、content，和标准 w3c 盒子模型不同的是：IE 盒子模型的 content 部分包含了 border 和 pading。 
```
16、flex布局模型

```
https://css-tricks.com/snippets/css/a-guide-to-flexbox/
http://www.houyuewei.cn/?s=flex&submit=%E6%90%9C%E7%B4%A2
```
17、line-height和font-size的关系

```
参考：
https://www.w3cplus.com/css/css-font-metrics-line-height-and-vertical-align.html

http://www.zhangxinxu.com/wordpress/2009/11/css%E8%A1%8C%E9%AB%98line-height%E7%9A%84%E4%B8%80%E4%BA%9B%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%8F%8A%E5%BA%94%E7%94%A8/

http://www.studyofnet.com/news/273.html
```
18、用纯CSS创建一个三角形的原理是什么？

```
把上、左、右三条边隐藏掉（颜色设为 transparent）
#demo { width: 0; height: 0; border-width: 20px; border-style: solid; border-color: transparent transparent red transparent;}
```
19、一个满屏 品 字布局 如何设计?
```
上面的div宽100%， 下面的两个div分别宽50%， 然后将右下的设置为float：right使其不换行即可
```
20、经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？

```
1)png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8
2)浏览器默认的margin和padding不同。解决方案是使用全局样式统一
3）IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。 浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 10px;} 这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性
4）IE下,可以使用 {对象.属性} 的方法来获取自定义属性, 也可以使用getAttribute()获取自定义属性; Firefox下,只能使用getAttribute()获取自定义属性。 解决方法:统一通过getAttribute()获取自定义属性。
5）IE下,even对象有x,y属性,但是没有pageX,pageY属性; Firefox下,event对象有pageX,pageY属性,但是没有x,y属性
```
21、absolute的containing block(容器块)计算方式跟正常流有什么不同？

```
无论属于哪种，都要先找到其祖先元素中最近的 position 值不为 static 的元素，然后再判断：1、若此元素为 inline 元素，则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；
2、否则,则由这个祖先元素的 padding box 构成。如果都找不到，则为 initial containing block。
补充：
1. static(默认的)/relative：简单说就是它的父元素的内容框（即去掉padding的部分）2. absolute: 向上找最近的定位为absolute/relative的元素
3. fixed: 它的containing block一律为根元素(html/body)，根元素也是initial containing block
```
22、CSS里的visibility属性有个collapse属性值的作用？在不同浏览器下以后什么区别？

```
用于表格行、列、列组和行组，隐藏表格的行或列，并且不占用任何空间（与将 display: none 用于表格的行/列上的效果相当）。但是其他行与列的宽和高不会重新计算，行与列的宽高计算依然会将被设为 collapse 的行和列考虑进去。这是用于快速从表格中删除一行或一列，而无需重新计算表格其他元素的宽和高

有些现代浏览器对 visibility: collapse 不支持或是不完全支持。很多时候用在不是表格行与列的元素上时不会正确的将它显示成 visibility: hidden 的效果。
visibility:collapse 会改变表格的布局，嵌套在其被折叠的单元格中的表格也会同样被折叠，除非专门为此嵌套表格指定 visibility: visible 。
```
23、position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样

```
参考：http://www.cnblogs.com/jackyWHJ/p/3756087.html
```
24、对BFC规范(块级格式化上下文：block formatting context)的理解？

```
（W3C CSS 2.1 规范中的一个概念,它是一个独立容器，决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。） 一个页面是由很多个 Box 组成的,元素的类型和 display 属性,决定了这个 Box 的类型。 不同类型的 Box,会参与不同的 Formatting Context（决定如何渲染文档的容器）,因此Box内的元素会以不同的方式渲染,也就是说BFC内部的元素和外部的元素不会互相影响。
```
25、css定义的权重

```
标签的权重为1，class的权重为10，id的权重为100
```
26、浏览器是怎样解析CSS选择器的？

```
参考：http://www.cnblogs.com/zhaodongyu/p/3341080.html
```
27、::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用

```
单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。
伪类用于向某些选择器添加特殊的效果，与选择器相关。
伪元素用于将特殊的效果添加到某些选择器，添加一些特殊的效果

伪类的效果可以通过添加一个实际的类来达到，而伪元素的效果则需要通过添加一个实际的元素才能达到，这也是为什么他们一个称为伪类，一个称为伪元素的原因。
```
28、如何修改chrome记住密码后自动填充表单的黄色背景 ？

```
input:-webkit-autofill, textarea:-webkit-autofill, select:-webkit-autofill {
  background-color: rgb(250, 255, 189); /* #FAFFBD; */
  background-image: none;
  color: rgb(0, 0, 0);
}
```
29、你对line-height是如何理解的？

```
参考：http://www.zhangxinxu.com/wordpress/2009/11/css%E8%A1%8C%E9%AB%98line-height%E7%9A%84%E4%B8%80%E4%BA%9B%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%8F%8A%E5%BA%94%E7%94%A8/

```
30、如果需要手动写动画，你认为最小时间间隔是多久，为什么？

```
多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms
```
31、什么是Cookie 隔离？

```
如果静态文件都放在主域名下，那静态文件请求的时候都带有的cookie的数据提交给server的，非常
浪费流量，所以不如隔离开。
因为cookie有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有
cookie数据，这样可以降低请求头的大小，降低请求时间，从而达到降低整体请求延时的目的。
同时这种方式不会将cookie传入Web Server，也减少了Web Server对cookie的处理分析环节，
提高了webserver的http请求的解析速度。

```
32、cookie和本地存储的区别：

```
1) cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
2) cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下。存储大小限制也不同，cookie数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如会话标识。sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
3) 数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。
4) 作用域不同，sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；localStorage 在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的。Web Storage 支持事件通知机制，可以将数据更新的通知发送给监听者。Web Storage 的 api 接口使用更方便。
```
33、什么是CSS 预处理器 / 后处理器

```
- 预处理器例如：LESS、Sass、Stylus，用来预编译Sass或less，增强了css代码的复用性，还有
  层级、mixin、变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。
- 后处理器例如：PostCSS，通常被视为在完成的样式表中根据CSS规范处理CSS，让其更有效；目前
  最常做的是给CSS属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。
```
34、CSS hack

```
https://www.sitepoint.com/what-is-the-definition-of-a-css-hack/

http://www.cnblogs.com/PeunZhang/archive/2012/04/09/2437563.html
```
35、css透明问题

```
参考：
http://www.cnblogs.com/PeunZhang/p/4089894.html
```

36、div+css的布局较table布局有什么优点？

```
改版的时候更方便 只要改css文件。
页面加载速度更快、结构化清晰、页面显示简洁。
表现与结构相分离。
易于优化（seo）搜索引擎更友好
```
37、webP图片

```
https://isux.tencent.com/introduction-of-webp.html
```
38、知道什么是微格式吗？具体有几种，谈谈理解。在前端构建中应该考虑微格式吗？

```
微格式（Microformats）是一种让机器可读的语义化XHTML词汇的集合，是结构化数据的开放标准。是为特殊应用而制定的特殊格式。微格式目前的应用并不广泛，大多数的网站都是采用自己定义的格式来书写.微格式其实并不是浏览器或者HTML的某种标准，而是很多人进行起草创建的。它帮助我们更有效的管理前端代码，不仅让人能够读取其中的信息，也能让机器理解（典型的比如爬虫)

分类：vcard,hcard, hcalender
http://microformats.org/code/hcard/creator

优点：将智能数据添加到网页上，让网站内容在搜索引擎结果界面可以显示额外的提示。
```
39、一个页面上有大量的图片，加载很慢，你有哪些方法优化这些图片的加载，给用户更好的体验

```
1)图片懒加载，在页面上的未可视区域可以添加一个滚动条事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。
2)如果为幻灯片、相册等，可以使用图片预加载技术，将当前展示图片的前一张和后一张优先下载。
如果图片为css图片，可以使用CSSsprite，SVGsprite，Iconfont、Base64等技术。
3)如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。
4)如果图片展示区域小于图片的真实大小，则因在服务器端根据业务需要先行进行图片压缩，图片压缩后大小与展示一致。
```
40、你如何理解HTML结构的语义化？

```
1)去掉或样式丢失的时候能让页面呈现清晰的结构
2)屏幕阅读器会完全根据你的标记来“读”你的网页.
3)搜索引擎的爬虫也依赖于标记来确定上下文和各个关键字的权重
4)便于团队开发和维护

```
41、行内元素的padding和margin可设置吗？

```
宽度(width)、高度(height)、内边距的top/bottom(padding-top/padding-bottom)和外边距的top/bottom(margin-top/margin-bottom)都不可改变, 
padding和margin的left和right是可以设置的，就是里面文字或图片的大小
```
42、rgba()和opacity的透明效果有什么不同？

```
rgba()和opacity都能实现透明效果，但最大的不同是opacity作用于元素，以及元素内的所有内容的透明度，
而rgba()只作用于元素的颜色或其背景色。（设置rgba透明的元素的子元素不会继承透明效果！）
```
43、如何垂直居中一个浮动元素？

```
// 方法一：已知元素的高宽
#ele{
    background-color:#6699FF;
    width:200px;
    height:200px;
    position: absolute;        //父元素需要绝对定位
    top: 50%;
    left: 50%;
    margin-top:-100px ;   //二分之一的height，width
    margin-left: -100px;
 }
 
//方法二:未知元素的高宽
  #ele{
    width: 200px;
    height: 200px;
    background-color: #6699FF;
    margin:auto;
    position: absolute;        //父元素需要绝对定位
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
  }
```