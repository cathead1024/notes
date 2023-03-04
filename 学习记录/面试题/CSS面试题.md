## CSS盒模型

- 盒子的组成：内容（content）、内边距（padding）、边框（border）、外边距（margin）
- 盒子的类型：
  - **标准盒模型**
    - content+padding+border+margin
  - **IE盒模型**
    - (content+padding+border)+margin
- 修改盒子的方式：
  - box-sizing：
    - content-box ：标准盒模型（默认属性）
    - border-box：怪异盒模型

## 重排（回流）和重绘

概念

- **重排**：当DOM的变化影响了元素的几何信息(元素的的位置和尺寸大小)，浏览器需要重新计算元素的几何属性，将其安放在界面中的正确位置，这个过程叫做重排。
- **重绘**：根据渲染树和重排的几何信息，得到绝对像素

如何触发

- **重排**：页面信息改变的时候就会触发，比如删除添加元素 、视口、元素尺寸或位置改变等....
- 重绘：触发重排是一定会触发重绘，元素颜色的改变、阴影的改变、文本方向的改变也会触发重绘。

如何减少

- 使用css中的动画相关的属性
- 多元素添加的时候使用文档碎片
- 避免使用table
- 使用复杂属性的时候尽量，使用absolute或flxed脱离文档流。
- 还可以使用离线操作，把元素的display设置为none。然后再进行操作， 操作完成后再设置为非none的属性。这样就只触发一次

## z-index在什么情况下会失效

- 当父元素定位是: relative

- 本身元素是默认定位（static），没有设置定位的时候
- 元素设置了z-index的同时还设置了浮动。

## position:fixed;一定是相对于浏览器窗口定位的吗

不一定，position:fixed;是指定元素相对于视口进行定位的，如果它的祖先元素设置了动画（transfrom）滤镜（fuilter）还有一个3D属性，的情况下，Position:fixed; 相对定位就会改变

## CSS3有什么新特性

- 背景图片相关：background-image background-repeat backgound-size background-orgin等
- 媒体查询：@media 通过特定规则显示不同的样式
- 圆角：border-radius
- 盒子阴影：box-sizing
- 文字阴影、单词换行：font-sizing、word-warp等
- 边框图片：border-images

## style 标签写在 body 后与 body 前有什么区别？

**写在body前**：有利于浏览器逐步渲染。

**写在body后**：当浏览器解析HTML并构建DOM的时候遇到Style标签的时候会中断解析（解析），这个时候浏览器就会等待Style里面的样式解析并渲染完成之后再重新构建。就不利于浏览器的渲染，影响浏览器的性能。

## CSS选择器及优先级

**选择器**：

1. 类选择器：.class
2. id选择器：#id
3. 标签选择器 div
4. 属性选择器 input[name="xxx"]
5. 伪类选择器 a:hover a:nth-child
6. 伪元素选择器 :befor :after
7. 子选择器 div p
8. 后代选择器 div > p
9. 相邻选择器 div + p
10. 深度选择器 /deep/ ::v-deep
11. 通配符选择器 *

**优先级**

!important 优先级最高

- 内联样式（1000）
- ID选择器（100）
- 类选择器 / 属性选择器 / 伪类选择器（10）
- 标签选择器 / 伪元素选择器（1）
- 关系选择器 / 通配符选择器（0）	

## rgba() 和 opacity 设置透明度的区别是什么？

**rgba()**

​	只针对颜色值的透明，不会改变里面内容的透明

**opacity**

​	设置该属性的元素及其里面的内容都会被透明化，是可以被继承的。

## 浏览器是如何解析 css 选择器的？

从右往左来解析CSS选择器，先找到最里面的子节点，然后向上寻找其父节点直到找到根节点或满足条件的匹配。

如果从左往右找，如果没找到就要回溯，这样会损失大量的性能。不利于构建渲染树。

但解析完CSS规则树之后会和DOM树结合并建立出渲染树，然后进行绘图。

## display: none 和 visibility: hidden 两者的区别

- display:none不能被继承，visibility:hidden 可以被继承
- display:none会引起重排，而visibility只会引起重绘
- display:none;不占据文档流，而visibility还是占据着文档流
- transition 可以作用于visibility，但不能作用于display:none

## 简述 transform，transition，animation 的作用

1. transform是CSS3的特性，用于描述元素的静态样式，可以让元素具备 旋转 位移 变形 缩放等操作，通常配合 Animation和traisition 来实现动画效果。
2. transition用于设置过渡效果，是一个合写属性。从左到右分别是 过渡效果的css属性名称、过渡效果花费时间、速度曲线、过渡开始的延迟时间，通常用来配合transition或者伪类或别的东西，需要由事件触发
3. animation：动画，使用@keyframes来描述每一帧的内容

## line-height 如何继承？

1. 父元素的line-height是固定数值，或者是比例就直接继承
2. 父元素的line-height是百分比，则子元素的line-height为 父元素的font-size*百分比

## 如何让 chrome 支持 10px 的文字？

- 使用`transofrom:scale()`来缩放
- 例如：12px 就 transform:scale(.84)

## position 属性的值有哪些？

1. **static：**默认值,margin left top right bottom 不生效
2. **realtive：**相对定位，移动元素后，还是会占据文档流中的位置
3. **absolute：**绝对定位，相对于最近的relative定位，脱离文档流，移动元素会覆盖其它元素，不会占据位置
4. **fixed：**固定定位。元素的位置相对于浏览器窗口是固定位置，即使窗口滚动它也不会移动。固定定位的元素会脱离文档流，不占据空间，会与其他元素重叠。
5. **stick：**粘性定位可以被认为是相对定位和固定定位的混合，元素在跨越特定阈值前为相对定位，之后为固定定位。top，right，buttom，left，必须指定这四个阈值中的一个，才可以使粘性定位生效，否则行为与其相对定位相同。
6. **inherit ：**继承，子元素可以继承父元素的定位

## 介绍一下BFC



## 让一个元素水平/垂直居中的方法

>**水平居中**

​	行内元素：text-align:center;	

- **宽度确定的块元素**：

  - 使用 width和margin

    - ```css
      .class{
          width:1024px;// 注意一定要设置好宽度
          margin: 0 auto;
      }
      ```

  - 使用绝对定位和margin-left 

    - ```css
      .class{
          position:absolute;
          width:1024px;
          margin-left:calc((父元素的宽度  - 子元素的宽度) / 2); // 前提是父元素必须是relative
      }
      ```

- 宽度不确定的情况下

- 对于宽度未知的块级元素

  - table 标签配合 margin 左右 auto 实现
  - inline-block 实现：`display: inline-block; text-align: center;`
  - 绝对定位和 transform 实现， translateX 可以移动本身元素的50%
  - flex 布局 `justify-content: center`

>**垂直居中**

- 纯文字类，设置 line-height 等于 height
- 子绝父相，子元素通过 margin 实现自适应居中
- 子绝父相，通过位移 transform 实现
- flex 布局，`align-items: center;`
- table 布局，父级通过转换为表格形式，子级设置 vertical-align 实现	

## box-sizing属性

- `content-box`：标准盒模型，默认值
- `border-box`：IE盒模型
- `inherit`：继承

## 介绍一下flex布局

## 介绍一下grid布局

## 怎么清除浮动

1. 设置一个子标签属性设置为

   ```html
   <div style="clear:both"> 
   </div>
   ```

   - 缺点就是会产生很多没有意义的标签

2. 使用overflow和zoom 

   ```css
   .class{
       overflow:hidden;
       zoom:1;
   }
   ```

   - 缺点就是当内容超出容器的时候就会显示不见

3. 还是第一种方式，只不过是通过伪类来设置

   ```css
   .class:after{
       content:'';
       height:0;
       visiblity:hidden;
       clear:both;
       display:block;
   }
   ```

## css 中优雅降级和渐进增强有什么区别？

**优雅降级**：一开始就构建完整的功能，之后再根据其他浏览器进行测试和修复

**渐进增强**：一开始的时候先对低版本的浏览器进行开发，完成基本功能后，再对高版本的浏览器追加效果、交互，追加功能开发。

## img 的 alt 和 title 的异同？实现图片懒加载的原理？

1. alt是图片记载不出来的时候显示的文字。
2. title是鼠标放到图片上去之后显示的文字。
3. alt是必须的，而title不是必须的。

>图片懒加载的原理

先用data-xxx属性设置一下图片url地址，让img标签一开始的时候不加载图片，使用js监听滚动条的位置，等img快出现到浏览器视口的时候，再加载图片。

## 介绍一下雪碧图

- 雪碧图就是，把很多小图标集成到一个大的图片里面去，然后通过background-size和background-position等属性，控制图片的显示，从而达到显示的效果。

>**优缺点**

- 优点：
  - 可以减少图片的体积，同时也减少了http的请求次数
- 缺点：
  - 维护比较麻烦，容易失真模糊。

## 什么是字体图标

字体图标就是一种特殊的字体，通过这种字体，可以再页面上显示各种各样的图标，同时还可以使用color、font-size等字体、颜色属性来给字体图标设置样式，十分的方便。

## 浏览器的前缀，兼容性相关

在项目开发中，建议使用插件来自动添加前缀

- mozilla(firefox、flock等): -moz
- webkit 内核(safari、chrome等): -webkit
- opera 内核(opera浏览器): -o
- trident 内核(ie 浏览器): -ms
