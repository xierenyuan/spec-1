# scss 编码规范 [待修订]
> 理论上css 以遵循已下 规定。 参考 `百度FE`,腾讯FE 设定。大部分来自各位工程师良好的习惯 希望大家共同遵守

* [1 前言](#1-前言)                 
* [2 代码风格](#2-代码风格)     
   - [2.1 文件](#21-文件)    
   - [2.2 结构](#22-结构)  
   - [2.3 命名规则](#23-命名规则)
   - [2.4 注释](#24-注释)
   - [2.5 属性声明顺序](#25-属性声明顺序)  
   - [2.6 颜色](#26-颜色)          
   - [2.7 属性简写](#27-属性简写)          
   - [2.8 媒体查询](#28-媒体查询)          
   - [2.9 字体](#29-字体)          
   - [2.10 字号](#210-字号)          
* [3 通用](#3-通用)                  

## 1 前言
> 本文档的目的是使 `css`,`scss` 风格一致，容易被理解和被维护。主要针对scss 编写 规范。

## 2 代码风格

### 2.1 文件
####  CSS 文件使用无 BOM 的 UTF-8 编码。     
  > UTF-8 编码具有更广泛的适应性。BOM 在使用程序或工具处理文件时可能造成不必要的干扰。  
  
  scss 设置编码 方式   
  ```css 
  @charset "UTF-8";
  ```

####  非css 的文件 的使用 `*.scss` 为后缀     
  > scss 的编写风格 通常比sass 更容易让人接受 

### 2.2 结构
  > 指缩进 空格等 

####   缩进   
#####   使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。     
  
  ```css
    .element {
        position: absolute;
        top: 10px;
        left: 10px;

        border-radius: 10px;
        width: 50px;
        height: 50px;
    }  
  ```

####  空格
#####  以下几种情况不需要空格
  * 属性名后  
  * 多个规则的分隔符','前  
  * !important '!'后  
  * 属性值中'('后和')'前  
  * 行末不要有多余的空格  

##### 以下几种情况需要空格
  * 属性值前      
  * 选择器'>', '+', '~'前后      
  * '{'前     
  * @else 前后  
  * 属性值中的','后  
  * 注释'/*'后和'*/'前  

  ```css  
    /* not good */
    .element {
        color :red! important;
        background-color: rgba(0,0,0,.5);
    }

    /* good */
    .element {
        color: red !important;
        background-color: rgba(0, 0, 0, .5);
    }

    /* not good */
    .element ,
    .dialog{
        ...
    }

    /* good */
    .element,
    .dialog {

    }

    /* not good */
    .element>.dialog{
        ...
    }

    /* good */
    .element > .dialog{
        ...
    }

    /* not good */
    .element{
        ...
    }

    /* good */
    .element {
        ...
    }

    /* not good */
    @if{
        ...
    }@else{
        ...
    }

    /* good */
    @if {
        ...
    } @else {
        ...
    }
  ```
 
 #### 空行 
 ##### 以下几种情况需要空行：  
 * 文件最后保留一个空行    
 * '}'后最好跟一个空行，包括scss中嵌套的规则    
 * 属性之间需要适当的空行， 

 ```css  
    /* not good */
    .element {
        ...
    }
    .dialog {
        color: red;
        &:after {
            ...
        }
    }

    /* good */
    .element {
        ...
    }

    .dialog {
        color: red;

        &:after {
            ...
        }
    }   
 ```

 #### 换行
 ##### 以下几种情况不需要换行：  
  * '{'前  

 ##### 以下几种情况需要换行：
  * '{'后和'}'前  
  * 每个属性独占一行  
  * 多个规则的分隔符','后  

 ```css  
   /* not good */
    .element
    {color: red; background-color: black;}

    /* good */
    .element {
        color: red;
        background-color: black;
    }

    /* not good */
    .element, .dialog {
        ...
    }

    /* good */
    .element,
    .dialog {
        ...
    }  
 ```

  * 对于超长的样式，在样式值的 空格 处或 , 后换行，建议按逻辑分组   

  ``` css  
  /* 不同属性值按逻辑分组 */
    background:
        transparent url(aVeryVeryVeryLongUrlIsPlacedHere)
        no-repeat 0 0;

    /* 可重复多次的属性，每次重复一行 */
    background-image:
        url(aVeryVeryVeryLongUrlIsPlacedHere)
        url(anotherVeryVeryVeryLongUrlIsPlacedHere);

    /* 类似函数的属性值可以根据函数调用的缩进进行 */
    background-image: -webkit-gradient(
        linear,
        left bottom,
        left top,
        color-stop(0.04, rgb(88,94,124)),
        color-stop(0.52, rgb(115,123,162))
    );
  ```  

  #### 属性选择器中的值必须用双引号包围
  > 不允许使用单引号 

  ``` css 
     /* good */
    article[character="juliet"] {
        voice-family: "Vivien Leigh", victoria, female;
    }

    /* bad */
    article[character='juliet'] {
        voice-family: "Vivien Leigh", victoria, female;
    }

    .element:after {
        content: "";
        background-image: url("logo.png");
    }

    li[data-type="single"] {
        ...
    }
  ```

  #### 属性定义后必须以分号结尾 

  ``` css
  /* good */
    .selector {
        margin: 0;
    }

    /* bad */
    .selector {
        margin: 0
    }
  ```
  ### 2.3 命名规则

  #### 类名使用小写字母，以中划线分隔

  ```css  
     /* class */
    .element-content {
        ...
    }
  ```

  #### id采用驼峰式命名

  ```css 
    /* id */
    #myDialog {
        ...
    }
  ```

  #### scss中的变量、函数、混合、placeholder采用驼峰式命名

  ```scss 
     /* 变量 */
    $colorBlack: #000;

    /* 函数 */
    @function pxToRem($px) {
        ...
    }

    /* 混合 */
    @mixin centerBlock {
        ...
    }

    /* placeholder */
    %myDialog {
        ...
    }
  ```

  #### 目录/文件命名

  * 全部采用小写方式，以`.` 分隔   
    * `第三方`引入的库 不受此规定限制
  * 有复数结构时，要采用复数命名法。 
  * 私有文件 以 下划线 `_` 开头
  
  ```
    scss 
      -- commons
         -- header.scss 
         -- footer.scss 
      -- utils 
         -- _layout.scss 
      -- cof
         -- rrc.blue.theme.scss   
  ```

  ### 2.4 注释

  #### 注释统一用'/* */'（scss中也不要用'//'
  #### 缩进与下一行代码保持一致；
  #### 可位于一个代码行的末尾，与代码间隔一个空格。

  ``` css 
    /* Modal header */
    .modal-header {
        ...
    }

    /*
    * Modal header
    */
    .modal-header {
        ...
    }

    .modal-header {
        /* 50px */
        width: 50px;

        color: red; /* color red */
    }
  ```   

  ### 2.5 属性声明顺序
  * 相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。
  > 摘自 腾讯 FE

  ``` css
    .declaration-order {
        display: block;
        float: right;

        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        z-index: 100;

        border: 1px solid #e5e5e5;
        border-radius: 3px;
        width: 100px;
        height: 100px;

        font: normal 13px "Helvetica Neue", sans-serif;
        line-height: 1.5;
        text-align: center;

        color: #333;
        background-color: #f5f5f5;

        opacity: 1;
    }

  ```

  * 下面是推荐的属性的顺序
  ```json
    // 下面是推荐的属性的顺序
    [
        [
            "display",
            "visibility",
            "float",
            "clear",
            "overflow",
            "overflow-x",
            "overflow-y",
            "clip",
            "zoom"
        ],
        [
            "table-layout",
            "empty-cells",
            "caption-side",
            "border-spacing",
            "border-collapse",
            "list-style",
            "list-style-position",
            "list-style-type",
            "list-style-image"
        ],
        [
            "-webkit-box-orient",
            "-webkit-box-direction",
            "-webkit-box-decoration-break",
            "-webkit-box-pack",
            "-webkit-box-align",
            "-webkit-box-flex"
        ],
        [
            "position",
            "top",
            "right",
            "bottom",
            "left",
            "z-index"
        ],
        [
            "margin",
            "margin-top",
            "margin-right",
            "margin-bottom",
            "margin-left",
            "-webkit-box-sizing",
            "-moz-box-sizing",
            "box-sizing",
            "border",
            "border-width",
            "border-style",
            "border-color",
            "border-top",
            "border-top-width",
            "border-top-style",
            "border-top-color",
            "border-right",
            "border-right-width",
            "border-right-style",
            "border-right-color",
            "border-bottom",
            "border-bottom-width",
            "border-bottom-style",
            "border-bottom-color",
            "border-left",
            "border-left-width",
            "border-left-style",
            "border-left-color",
            "-webkit-border-radius",
            "-moz-border-radius",
            "border-radius",
            "-webkit-border-top-left-radius",
            "-moz-border-radius-topleft",
            "border-top-left-radius",
            "-webkit-border-top-right-radius",
            "-moz-border-radius-topright",
            "border-top-right-radius",
            "-webkit-border-bottom-right-radius",
            "-moz-border-radius-bottomright",
            "border-bottom-right-radius",
            "-webkit-border-bottom-left-radius",
            "-moz-border-radius-bottomleft",
            "border-bottom-left-radius",
            "-webkit-border-image",
            "-moz-border-image",
            "-o-border-image",
            "border-image",
            "-webkit-border-image-source",
            "-moz-border-image-source",
            "-o-border-image-source",
            "border-image-source",
            "-webkit-border-image-slice",
            "-moz-border-image-slice",
            "-o-border-image-slice",
            "border-image-slice",
            "-webkit-border-image-width",
            "-moz-border-image-width",
            "-o-border-image-width",
            "border-image-width",
            "-webkit-border-image-outset",
            "-moz-border-image-outset",
            "-o-border-image-outset",
            "border-image-outset",
            "-webkit-border-image-repeat",
            "-moz-border-image-repeat",
            "-o-border-image-repeat",
            "border-image-repeat",
            "padding",
            "padding-top",
            "padding-right",
            "padding-bottom",
            "padding-left",
            "width",
            "min-width",
            "max-width",
            "height",
            "min-height",
            "max-height"
        ],
        [
            "font",
            "font-family",
            "font-size",
            "font-weight",
            "font-style",
            "font-variant",
            "font-size-adjust",
            "font-stretch",
            "font-effect",
            "font-emphasize",
            "font-emphasize-position",
            "font-emphasize-style",
            "font-smooth",
            "line-height",
            "text-align",
            "-webkit-text-align-last",
            "-moz-text-align-last",
            "-ms-text-align-last",
            "text-align-last",
            "vertical-align",
            "white-space",
            "text-decoration",
            "text-emphasis",
            "text-emphasis-color",
            "text-emphasis-style",
            "text-emphasis-position",
            "text-indent",
            "-ms-text-justify",
            "text-justify",
            "letter-spacing",
            "word-spacing",
            "-ms-writing-mode",
            "text-outline",
            "text-transform",
            "text-wrap",
            "-ms-text-overflow",
            "text-overflow",
            "text-overflow-ellipsis",
            "text-overflow-mode",
            "-ms-word-wrap",
            "word-wrap",
            "-ms-word-break",
            "word-break"
        ],
        [
            "color",
            "background",
            "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
            "background-color",
            "background-image",
            "background-repeat",
            "background-attachment",
            "background-position",
            "-ms-background-position-x",
            "background-position-x",
            "-ms-background-position-y",
            "background-position-y",
            "-webkit-background-clip",
            "-moz-background-clip",
            "background-clip",
            "background-origin",
            "-webkit-background-size",
            "-moz-background-size",
            "-o-background-size",
            "background-size"
        ],
        [
            "outline",
            "outline-width",
            "outline-style",
            "outline-color",
            "outline-offset",
            "opacity",
            "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
            "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
            "-ms-interpolation-mode",
            "-webkit-box-shadow",
            "-moz-box-shadow",
            "box-shadow",
            "filter:progid:DXImageTransform.Microsoft.gradient",
            "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
            "text-shadow"
        ],
        [
            "-webkit-transition",
            "-moz-transition",
            "-ms-transition",
            "-o-transition",
            "transition",
            "-webkit-transition-delay",
            "-moz-transition-delay",
            "-ms-transition-delay",
            "-o-transition-delay",
            "transition-delay",
            "-webkit-transition-timing-function",
            "-moz-transition-timing-function",
            "-ms-transition-timing-function",
            "-o-transition-timing-function",
            "transition-timing-function",
            "-webkit-transition-duration",
            "-moz-transition-duration",
            "-ms-transition-duration",
            "-o-transition-duration",
            "transition-duration",
            "-webkit-transition-property",
            "-moz-transition-property",
            "-ms-transition-property",
            "-o-transition-property",
            "transition-property",
            "-webkit-transform",
            "-moz-transform",
            "-ms-transform",
            "-o-transform",
            "transform",
            "-webkit-transform-origin",
            "-moz-transform-origin",
            "-ms-transform-origin",
            "-o-transform-origin",
            "transform-origin",
            "-webkit-animation",
            "-moz-animation",
            "-ms-animation",
            "-o-animation",
            "animation",
            "-webkit-animation-name",
            "-moz-animation-name",
            "-ms-animation-name",
            "-o-animation-name",
            "animation-name",
            "-webkit-animation-duration",
            "-moz-animation-duration",
            "-ms-animation-duration",
            "-o-animation-duration",
            "animation-duration",
            "-webkit-animation-play-state",
            "-moz-animation-play-state",
            "-ms-animation-play-state",
            "-o-animation-play-state",
            "animation-play-state",
            "-webkit-animation-timing-function",
            "-moz-animation-timing-function",
            "-ms-animation-timing-function",
            "-o-animation-timing-function",
            "animation-timing-function",
            "-webkit-animation-delay",
            "-moz-animation-delay",
            "-ms-animation-delay",
            "-o-animation-delay",
            "animation-delay",
            "-webkit-animation-iteration-count",
            "-moz-animation-iteration-count",
            "-ms-animation-iteration-count",
            "-o-animation-iteration-count",
            "animation-iteration-count",
            "-webkit-animation-direction",
            "-moz-animation-direction",
            "-ms-animation-direction",
            "-o-animation-direction",
            "animation-direction"
        ],
        [
            "content",
            "quotes",
            "counter-reset",
            "counter-increment",
            "resize",
            "cursor",
            "-webkit-user-select",
            "-moz-user-select",
            "-ms-user-select",
            "user-select",
            "nav-index",
            "nav-up",
            "nav-right",
            "nav-down",
            "nav-left",
            "-moz-tab-size",
            "-o-tab-size",
            "tab-size",
            "-webkit-hyphens",
            "-moz-hyphens",
            "hyphens",
            "pointer-events"
        ]
    ]
  ```

  ### 2.6 颜色

  #### 颜色16进制用小写字母； 
  #### 颜色16进制尽量用简写。

  ```css 
    /* not good */
    .element {
        color: #ABCDEF;
        background-color: #001122;
    }

    /* good */
    .element {
        color: #abcdef;
        background-color: #012;
    }
  ```

  ### 2.7 属性简写

  #### 属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；  
  `margin` 和 `padding` 相反，需要使用简写；  

  常见的属性简写包括   
  * font 
  * background 
  * transition  
  * animation  

  ```css 
    /* not good */
    .element {
        transition: opacity 1s linear 2s;
    }

    /* good */
    .element {
        transition-delay: 2s;
        transition-timing-function: linear;
        transition-duration: 1s;
        transition-property: opacity;
    }
  ```

  ### 2.8 媒体查询  

  #### 尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。  

  ```css 
    .element {
        ...
    }

    .element-avatar{
        ...
    }

    @media (min-width: 480px) {
        .element {
            ...
        }

        .element-avatar {
            ...
        }
    }
  ```

  ### 2.9 字体  
  > [参考](https://www.zhihu.com/question/19911793/answer/13329819)  
  * 常见名称
  
    | 字体         | 操作系统  | Family Name  | 
    | -----------  |:-------:| ----------:| 
    | 宋体(中易宋体) | Windows | SimSun | 
    | 黑体(中易黑体) | Windows |   SimHei | 
    | 微软雅黑      | Windows |    Microsoft YaHei | 
    | 微软正黑	    | Windows |    Microsoft JhengHei | 
    | 华文黑体      | Mac/iOS |    STHeiti | 
    | 冬青黑体      | Mac/iOS |    Hiragino Sans GB | 
    | 文泉驿正黑    | Linux     |    WenQuanYi Zen Hei | 
    | 文泉驿微米黑  | Linux     |    WenQuanYi Micro Hei | 
  


  #### `font-family` 属性中的字体族名称应使用字体的英文 Family Name，其中如有空格，须放置在引号中   
 
  ```css 
  h1 {
    font-family: "Microsoft YaHei";
  }
  ```
  #### `font-family` 按「西文字体在前、中文字体在后」、「效果佳 (质量高/更能满足需求) 的字体在前、效果一般的字体在后」的顺序编写，最后必须指定一个通用字体族( serif / sans-serif )。
  
  ```css 
    /* Display according to platform */
    .article {
        font-family: Arial, sans-serif;
    }

    /* Specific for most platforms */
    h1 {
        font-family: "Helvetica Neue", Arial, "Hiragino Sans GB", "WenQuanYi Micro Hei", "Microsoft YaHei", sans-serif;
    }
  ```

  #### font-family 不区分大小写，但在同一个项目中，同样的 Family Name 大小写必须统一。   

  ```css 
  /* good */
    body {
        font-family: Arial, sans-serif;
    }

    h1 {
        font-family: Arial, "Microsoft YaHei", sans-serif;
    }

    /* bad */
    body {
        font-family: arial, sans-serif;
    }

    h1 {
        font-family: Arial, "Microsoft YaHei", sans-serif;
    }
  ```

  ### 2.10 字号   

  #### 需要在 Windows 平台显示的中文内容，其字号应不小于 12px

  #### 字重应该设置在 700 
  > CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 400 和 700 两档，分别等价于关键词 normal 和 bold。  
  > 浏览器本身使用一系列启发式规则来进行匹配，在 <700 时一般匹配字体的 Regular 字重，>=700 时匹配 Bold 字重。   
  > 但已有浏览器开始支持 =600 时匹配 Semibold 字重 (见此表)，故使用数值描述增加了灵活性，也更简短。  

  ## 3 通用

  ###  代码组织  

  #### 代码按如下顺序组织： 
  1. `@import`
  2. 变量声明  
  3. 样式声明
     * @extend  
     * 不包含 @content 的 @include 
     * 包含 @content 的 @include  
     * 自身属性 
     * 嵌套规则   

  ```scss 
  @import 'theme/conf/mixins';

  $font-family: 'Roboto', sans-serif;

  .font {
      ...
  }
  ```

  #### @import 语句引用的文件必须写在一对引号内，引号使用 ' 和 " 均可，但在同一项目内必须统一   
  #### @import 引入的文件不需要开头的'_'和结尾的'.scss'；
  ```scss 
    @import "common";
    @import "theme/socicon";
    @import "theme/layout";/* 源文件 _layout.scss */
    @import 'theme/buttons';
    @import 'app/form';

    html {
      min-height: 520px;
      height: 100%;
    }

    body {
      @include main-background();
      height: 100%;
    }
  ```
  
  #### 【重要】 嵌套最多不能超过5层；

  #### 去掉不必要的父级引用符号'&'。

  ```scss  
    /* not good */
    .element {
        & > .dialog {
            ...
        }
    }

    /* good */
    .element {
        > .dialog {
            ...
        }
    }  
  ```
  
  ### 不允许有空的规则；

  ```scss 
     /* not good */
    .element {
    }
  ```

  ### 元素选择器用小写字母；

  ```scss 
   /* not good */
    LI {
        ...
    }

    /* good */
    li {
        ...
    }
  ```

  ### 去掉小数点前面的0；  

  ```scss 
    /* not good */
    .element {
        color: rgba(0, 0, 0, 0.5);
    }

    /* good */
    .element {
        color: rgba(0, 0, 0, .5);
    }

  ```
  
  ### 去掉数字中不必要的小数点和末尾的0；

  ```scss 
    /* not good */
    .element {
        width: 50.0px;
    }

    /* good */
    .element {
        width: 50px;
    }
  ```

  ### 属性值'0'后面不要加单位；

  ```scss 
    /* not good */
    .element {
        width: 0px;
    }

    /* good */
    .element {
        width: 0;
    }
  ```

  ### 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照下边的写法；

  ```scss 
    /* not good */
    .element {
        border-radius: 3px;
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;

        background: linear-gradient(to bottom, #fff 0, #eee 100%);
        background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
        background: -moz-linear-gradient(top, #fff 0, #eee 100%);
    }

    /* good */
    .element {
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;
                border-radius: 3px;

        background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
        background:    -moz-linear-gradient(top, #fff 0, #eee 100%);
        background:         linear-gradient(to bottom, #fff 0, #eee 100%);
    }

  ```

  ### 无前缀的标准属性应该写在有前缀的属性后面；

  ```scss  
    /* not good */
    .element {
        color: rgb(0, 0, 0);
        width: 50px;
        color: rgba(0, 0, 0, .5);
    }

    /* good */
    .element {
        color: rgb(0, 0, 0);
        color: rgba(0, 0, 0, .5);
    }
  ```

  ### 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

  ### 不要在一个文件里出现两个相同的规则；

  ### 用 border: 0; 代替 border: none;
 
  ### 选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；

  ### 发布的代码中不要有 @import

  ### 尽量少用'*'选择器。



 
  



  



  
