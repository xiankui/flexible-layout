# 移动端弹性布局的css实现方式

## 需要解决的两个问题
* 页面的布局
* 元素的适配

页面布局可以使用css flex属性或者百分比；下面重点解决的是元素的适配问题：

```
// 假设设计图的尺寸为750px 某元素尺寸为98px
var _VW = 750;
var originSize = 98;

// 那么我们只需要知道当前渲染屏幕的尺寸，即可对元素进行适配
var VW = ?;
var adaptationSize = (? / 750) * 98;

// 那么现在的问题就是怎么样得到viewport的尺寸？

// 第一种方法：yes vw
VW = 100vw;

// 第二种方法：通过css media query使得VW = 10rem
@media (min-width: 320px) {
    html {
        font-size: 32px }}
        
@media (min-width: 360px) {
    html {
        font-size: 36px }}
        
...

VW = 10rem

```

## [flex](http://caniuse.com/#search=flex) + [vw](http://caniuse.com/#search=vw) 
弹性布局 + 屏幕相对尺寸适配是一种先进的解决方式，参考演示[index.vw.html]；但是有一个问题：兼容性


## 用js根据viewport的变化，而对页面进行缩放
效果很好，但是对页面进行缩放让人感觉怪异；[实现方式](https://github.com/amfe/lib-flexible)

## 用css media query进行适
缺点：需罗列手机尺寸
本例就是对这种方式的演示[index.html]


## 一些参考
* [理解viewport](http://weizhifeng.net/viewports.html)

---

知识点：根节点的字体大小就是1rem

```
/* 1rem == 32px */
html { font-size: 32px; }
```