# CSS

**一、盒子模型**

标准盒子模型：width=content  盒子宽度=width+padding+border

<img src="\Images\标准盒子模型.jpg" style="zoom:80%;" />

IE盒子模型：width=content+padding+border  盒子宽度=width

<img src="\Images\IE盒子模型.jpg" style="zoom:80%;" />

**二、设置一个元素的背景颜色，背景颜色会填充哪些区域？**

background-color设置的背景颜色会填充元素的content、padding和border区域

**三、CSS有哪些选择器？优先级如何？**

id选择器、类选择器、标签选择器、伪类选择器、伪元素选择器、通用选择器（*）

内联样式>id选择器>类选择器>标签选择器

带有!important标记的样式属性优先级最高

**四、根据样式表来源划分的优先级**

内联样式>内部样式>外部样式>浏览器用户自定义样式>浏览器默认样式

**五、@import和link标签作用和区别**

作用：都用来引入CSS样式

区别：

- @import由CSS提供；link属于HTML标签
- @import只有IE5+才能识别；link不存在兼容性问题
- 页面被加载时，link会同时被加载；@import会等到页面加载结束后加载
- link权重高于@import

**六、CSS3新增内容**

- CSS3边框：border-radius、box-shadow、border-image
- CSS3背景：background-size、background-origin（规定背景图片定位区域）
- CSS3文字效果：text-shadow、word-wrap（对长单词进行拆分并换行）
- CSS3 2D转换：transform: translate()、rotate()、scale()
- CSS3 3D转换：transform: rotateX()、rotateY()
- CSS3 过渡：transition
- CSS3 动画：animation
- CSS3用户界面：resize（是否可由用户调整元素尺寸）、box-sizing（定义盒模型）

**七、隐藏页面中某个元素的方法？**

opacity=0；visibility=hidden；display：none；position移到外部；z-index图层遮盖

**八、visibility=hidden, opacity=0, display:none区别**

- opacity=0：元素透明度为0，该元素被隐藏起来，但不会改变页面布局，如果该元素已经绑定一些事件，仍能触发
- visibility=hidden：元素不可见但仍然存在，不会改变页面布局，但不会触发该元素已经绑定的事件
- display:none：元素不显示并且会改变页面布局，可理解为该元素从页面中被删除

**九、z-index定位方法**

z-index只能在定位元素上奏效，该属性设置一个定位元素沿z轴的位置，如果为正数，离用户越近；为负数，离用户越远。默认值为auto，即堆叠顺序和父元素相等。其他属性值有number、inherit

**十、CSS动画如何实现？transition和animation的区别**

- 使用animation创建动画序列，该属性允许配置动画时间、时长以及其他动画细节，但不能配置动画的实际表现，动画的实际表现由@keyframes规则实现
- 使用transition实现，transition强调过渡，是元素的一个或多个属性发生变化时产生的过渡效果，同一个元素通过两个不同的途径获取样式，而当第二个途径发生某种改变时才会产生过渡动画

区别：

- transition需要触发一个事件才能改变属性；animation不需要触发任何事件就会随时间改变属性
- transition为2帧（from…to…）；animation可以一帧一帧的

参考：[CSS3 Transitions, Transforms和Animation使用简介与应用展示](https://www.zhangxinxu.com/wordpress/2010/11/css3-transitions-transforms-animation-introduction/)

**十一、transition有哪些属性？**

- transition-property：指定过渡的属性值
- transition-delay：指定延迟过渡时间
- transition-duration：指定过渡持续时间
- transition-timing-function：指定过渡动画缓动类型（ease-out/快-慢、ease-in/慢-快、ease-in-out/慢-快-慢、liner线性过渡、cubic-bezier贝塞尔曲线等）

**十二、js动画和css3动画区别**

|          |                             优点                             |                             缺点                             |
| :------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|  js动画  | 可在动画播放过程中对其进行开始、暂停、回放、终止、取消等控制；动画效果丰富，可以实现一些复杂效果，如视差滚动等；不存在兼容性问题 |        干扰主线程导致阻塞，造成丢帧情况；代码复杂度高        |
| css3动画 |           浏览器会对CSS3动画进行优化；代码相对简单           | CSS3动画只能暂停，运行过程控制较弱，无法附加事件绑定回调函数；代码冗长，部分动画无法实现；兼容性不好 |

**十三、position有哪些属性？**

| 属性               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| fixed(固定定位)    | 元素位置相对于浏览器窗口是固定的，即使窗口滚动也不会移动。fixed定位使元素脱离文档流，因此不占据空间。fixed定位元素会和其他元素重叠。 |
| absolute(绝对定位) | 元素位置相对于最近的已定位父元素，若没有则相对于html。absolute定位使元素位置脱离文档流，因此不占据空间。absolute定位元素和其他元素重叠。 |
| relative(相对定位) | 相对定位的元素将出现在它所在的位置上，然后可通过top、bottom、right、left让这个元素相对于它的初始位置移动。使用相对定位时无论元素是否移动仍占据原来空间，因此，移动元素会导致它覆盖其他框。 |
| sticky(粘性定位)   | 元素先按普通文档流进行定位，然后相对于该元素在流中的flow root（BFC）和containing block（最近块级祖先元素）定位。而后，元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。 |
| static(默认定位)   | 默认值，没有定位。元素出现在正常的流中（忽略top、bottom、right、left、z-index声明） |
| inherit            | 继承父元素的position属性值                                   |

**十三、inline-block、inline和block的区别？**

- block：块级元素，前后都有换行符，可设置width和height，padding和margin水平垂直方向均有效
- inline：内联元素，前后无换行符，在一排排列，不可设置width和height，垂直方向上padding和margin失效
- inline-block：内联块级元素，可设置width和height，padding和margin水平垂直方向均有效，前后无换行符

**十四、为什么img是inline还可以设置宽高**

img属于替换元素，替换元素一般有内在尺寸和宽高比，所以具有width和height，可设定

HTML中的替换元素：img、input、textarea、select

**十五、三种文档流**

普通流

- 普通流中，盒子一个接着一个排列
- 块级格式化上下文里，盒子竖着排列；行内格式化上下文中，盒子横着排列
- 当position为static或relative，并且float为none时会触发普通流
- position：static，盒的位置是常规流布局里的位置
- position：relative，盒偏移位置由top、bottom、left、right属性定义。即使有偏移，仍然保留原有位置，其他常规流不能占用这个位置

定位流

- 盒从常规流中被移除，不影响常规流的布局
- 当position为fixed或absolute时为绝对定位元素
- position：absolute，元素定位将相对于上级元素中最近的一个relative、fixed、absolute，如果没有则相对于body

浮动流

- 左浮动元素尽量靠左靠上，右浮动同理
- 除非设置clear，否则普通流环绕在其周围
- 浮动元素不影响块级元素的布局，但会影响行内元素的布局，让其围绕在自己周围，撑大父级元素，从而间接影响块级元素布局
- 浮动元素最高点不超过当前行的最高点和其前面的浮动元素的最高点；不超过它的包含块，除非元素本身已经比包含块更宽
- 行内元素只出现在左浮动元素的右边或右浮动元素的左边

**十六、页面布局方式**

| 方式                            | 布局特点                                                     | 设计方法                                                     | 缺点                                                         |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 静态布局（Static Layout）       | 无论浏览器尺寸具体多少，网页布局始终按照最初写代码时的布局来实现 | 居中布局，所有样式使用绝对宽度和高度px；屏幕宽高调整时通过滚动条来浏览被遮掩部分 | 不能根据用户的屏幕尺寸做出不同表现                           |
| 流式布局（Liquid Layout）       | 屏幕分辨率变化时，页面内元素的大小会变化而布局不变；屏幕太大或太小都会导致元素无法正常显示 | 使用%定义宽度，px定义高度，配合max-width/min-width控制尺寸流动范围以免过大或过小影响阅读 | 如果屏幕尺寸跨度太大，那么在相对其原始设计而言过小或过大的屏幕上不能正常显示 |
| 自适应布局（Adaptive Layout）   | 屏幕分辨率变化时，页面内元素的位置会变化而大小不会变化       | 创建多个静态布局，每个静态布局对应一个屏幕分辨率范围，屏幕分辨率改变时，切换不同的静态布局（通过@media媒体查询给不同尺寸的设备切换不同样式） | 需要需要为不同的设备开发不同的页面，增加开发成本；当需求改变时可能会改动多套代码，流程繁琐。 |
| 响应式布局（Responsive Layout） | 每个屏幕分辨率下会有一个布局样式，即屏幕分辨率变化时，元素位置和大小都会变 | @media媒体查询+流式布局                                      | 媒体查询是有限的，只能适应主流媒体的宽高                     |
| 弹性布局（rem/em布局）          | 包裹文字的各元素的尺寸采用rem/em做单位（em相对其父元素，rem始终相对html大小，即页面根元素），页面主要划分区域的尺寸仍使用百分数或px | 一般使用rem，根据屏幕大小来控制html元素的font-size，即可自动改变所有用rem定义尺寸的元素的大小 | 只做到了宽度自适应，无法满足一些对高度或者元素间距要求较高的设计 |

1. 流式布局VS响应式布局

   流式布局用于解决类似的设备不同分辨率之间的兼容（分辨率差异较小）；响应式布局用于解决不同设备之间不同分辨率的兼容（分辨率差异较大）

2. 自适应布局VS响应式布局

   共同点：检测设备，根据不同设备采用不同CSS，且CSS都采用百分比确定宽度

   区别：响应式布局在不同设备上看上去是不一样的，会随着设备的改变而改变展示样式；自适应布局在所有的设备上看上去是一样的模板，不过是长度或者图片变小了

参考：[静态布局、自适应布局、流式布局、响应式布局、弹性布局等的概念和区别](https://www.jianshu.com/p/0be6b9f77dd5)

**十七、BFC定义、触发条件（哪些元素会生成BFC）、约束规则、作用**

1. 定义：BFC块级格式化上下文，用于决定块盒子的布局及浮动相互影响范围的一个渲染区域
2. 触发方式/哪些元素会生成BFC

   - 根元素，即HTML标签

   - 浮动元素：float值为left或right

   - 定位元素：position为fixed或absolute的元素

   - overflow值不为visible，为auto、scroll、hidden的元素

   - display值为inline-block、table-cell、table-caption、flex、inline-flex的元素

3. 约束规则

   - 内部的box会在垂直方向上一个接一个放置

   - 内部的box垂直方向上的距离由margin决定

   - 每个元素的左外边距与包含块的左边界相接触，即使浮动元素也如此

   - BFC的区域不会与float的元素区域重叠

   - 计算BFC高度时，浮动元素也参与计算

4. 作用

   - 阻止元素被浮动元素覆盖

   - 可以包含浮动元素

   - 阻止因浏览器四舍五入造成的多列布局换行的情况

   - 阻止相邻元素margin合并

**十八、什么是浮动溢出？如何清除浮动？**

在非IE浏览器下，当容器的高度为auto，且容器中有浮动元素（float为left或right）时，容器的高度不能自动伸长以适应内容的高度，使得内容溢出到容器外面而影响甚至破坏布局。

CSS清除浮动方法：

- 在浮动元素后使用一个带clear属性的空元素
- 给浮动元素的容器添加overflow：hidden属性
- 使用:after伪元素

参考：[CSS技巧（一）：清除浮动](https://www.cnblogs.com/ForEvErNoME/p/3383539.html)

**十九、垂直居中方法**

1. 不知道子元素的宽度和高度

   容器display:flex; justify-content:center; align-items:center;

2. 知道子元素的宽度和高度

   - 容器position:relative;   
     子元素position:absolute; top:50%; left:50%; transform: translateX(-50%) translateY(-50%);

   - 容器position:relative;  
     子元素margin:auto; top:0; right:0; bottom:0; left:0;

**二十、flex布局**

flex布局，用来为盒模型提供最大灵活性（任何一个容器都可以指定为flex布局，设为flex布局后子元素的float、clear和vertical-align属性将失效）

flex容器（flex container）+flex项目（flex item）

![](/Images/flex布局.png)

注：水平轴为主轴（main axis），项目默认沿主轴排列

1. flex container属性（6个）
   - flex-direction：决定主轴方向，即项目的排列方向
   - flex-wrap：如果一条轴线排不下如何换行
   - flex-flow：flex-direction + flex-wrap
   - justify-content：定义项目在主轴上的对齐方式
   - align-items：定义项目在交叉轴上的对齐方式
   - align-content：定义多跟轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

2. flex item属性（6个）

   - order：定义项目排列顺序，数值越小排列越靠前，默认为0

   - flex-grow：定义项目放大比例，默认为0（如果存在剩余空间也不放大）

   - flex-shrink：定义项目缩小比例，默认为1（如果空间不足缩小该项目），负值对该属性无效

   - flex-basis：定义在分配多余空间之前，项目占据的主轴，默认auto（项目本来大小）

   - flex：flex-grow + flex-shrink + flex-basis

   - align-self：允许单个项目与其他项目不一样的对齐方式，可覆盖align-items，默认auto（继承父元素align-items属性，无父元素则等同于stretch）

参考：[Flex 布局教程：语法篇](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

**二十一、grid布局**

grid网格布局，它将页面划分成一个个网格，可以任意组合不同的网格。由容器和项目两部分组成，容器默认为块级元素，也可以通过inline-grid设置为行内元素；项目只能是容器的顶层子元素，不包含项目的子元素（设为网格布局后，容器子元素的float、display:inline-block | table-cell、vertical-align和column-*等设置都将失效）

参考：[CSS Grid 网格布局教程](http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)（grid布局的属性比较多，这里不具体列出来了，大家可以参考阮老师的这篇博客）

**二十二、grid布局和flex布局的区别**

flex布局是轴线布局，只能指定items针对轴线的位置，可以看作是一维布局；grid布局则是将容器划分为行和列，产生单元格，然后指定items所在的单元格，可以看作是二维布局。