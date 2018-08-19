# 流式布局
就是百分比布局，非固定像素，内容向两侧填充，理解成流动的布局，称为流式布局
# 视觉窗口
viewport,是移动端特有。这是一个虚拟的区域，承载网页的。
承载关系：浏览器---->viewport---->网页
       
# 适配要求
1. 网页宽度必须和浏览器保持一致
2. 默认显示的缩放比例和PC端保持（缩放比例1.0）
3. 不允许用户自行缩放网页
 满足这些要求达到了适配，国际上通用的适配方案，标准的移动端适配方案。
       
# 适配设置

如果任何设置都没有，默认走的就是viewport的默认设置
去设置新的viewport设置,达到适配要求。
```<meta name="viewport"> ```设置视口的标签  在head里面并且应该紧接着编码设置
## viewport的功能：
1. width    可以设置宽度   (device-width 当前设备的宽度)
2. height   可以设置高度
3. initial-scale  可以设置默认的缩放比例
4. user-scalable  可以设置是否允许用户自行缩放
5. maximum-scale  可以设置最大缩放比例
6. minimum-scale  可以设置最小缩放比例
在```<meta name="viewport" content="" >  content="" ```使用以上参数
1. width=device-width   宽度一致比例是1.0
2. initial-scale=1.0    宽度一致比例是1.0
3. user-scalable=no     不允许用户自行缩放  （yes，no  1,0）
标准适配方案：
```<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=0">```
meta:vp + tab  快捷方式
# 非主流的适配方案：
1. 页面的真实尺寸会比在设备的上尺寸要大几倍
2. 假设设备是iphone4 -> 320px -> 网页尺寸 640px
3. 缩放操作，有2倍的  有3倍  和屏幕像素比有关系
4. 什么是屏幕像素（物理像素，像素点） px(页面的尺寸单位)
5. 物理像素 是设备显示屏的最小可视颗粒的大小   以前的手机（直板手机）
6. 现在有 高清显示屏  视网膜屏  retina屏
7. 显示的效果就提高了更细腻，但是在显示同等质量的图片的时候（模糊效果）
8. 在屏幕像素比（一个px宽的屏幕能放几个物理像素）高的设备  图片（非矢量）显示会模糊
9. 提高网页的清晰度  根据屏幕的像素比 来缩放网页
10. 但是这样的适配方案成本非常高
11. 一般的企业开发当中使用的还是标准化设置
在高清显示屏当中：图片可能会失真（模糊）

# 不建议在移动端使用jquery
1. 可以使用jquery,但是不建议
2. jquery  做了很多桌面浏览器的兼容问题 特别是IE，但是移动端没有IE浏览器
3. 主流的浏览器：谷歌 火狐（2016年停止了维护和更新） safari浏览器  百度  360 qq ...
4. 特点：内核基本上都是  webkit  或者 blink  兼容  -webkit-
5. 使用H5的api 或者说使用一个 叫做： zepto.js 的库（基于高版本浏览器开发）
# box-sizing
1. 移动端以流式布局为主
2. 百分比布局
3. 非固定像素布局
4. 无法准确计算容器的尺寸
```
 *{
    margin: 0;
    padding: 0;
}
.box{
    width: 100%;
    border: 20px solid pink;
    height: 1000px;
    /*防止内容溢出  不出现滚动条  提供用户体验*/
    box-sizing: border-box;
}
```
# 点击高亮
```
 /*轻击 轻触*/
-webkit-tap-highlight-color: red;
```

# base.css
```
/*=======reset css========*/
*,
*::before,
*::after{
    /*所有的标签，和伪元素都选中*/
    margin: 0;
    padding: 0;
    /*移动端常用布局是非固定像素*/
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    /*点击高亮效果的清除*/
    tap-highlight-color: transparent;
    -webkit-tap-highlight-color: transparent;
}

/*使用精灵图的公用样式*/
[class^="icon_"],[class*=" icon_"]{
    background-repeat: no-repeat;
    background-image: url("../images/sprites.png");
    background-size: 200px 200px;
}
```