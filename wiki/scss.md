# scss 编码规范
> 理论上css 以遵循已下 规定。

* [1 前言](#1-前言)                 
* [2 代码风格](#2-代码风格)     
   - [2.1 文件](#21-文件)    
   - [2.2 结构](#22-结构)  
   - [2.3 命名规则](#23-命名规则)
   - [2.4 注释](#24-注释)
   - [2.2 结构](#22-结构)    
* [3 语言特性](#3-语言特性)                  
   - [3.1 类型](#31-类型)               
   - [3.2 引用](#32-引用)                 
   - [3.3 对象](#33-对象)     
   - [3.4 解构](#34-解构)  
   - [3.5 字符串模板](#35-字符串模板)  
   - [3.6 函数](#36-函数)  
   - [3.7 箭头函数](#37-箭头函数)     
   - [3.8 构造器](#38-构造器)   
   - [3.9 模块](#39-模块)   
   - [3.10 对象](#310-对象)             
   - [3.11 集合](#311-集合)            
   - [3.12 异步](#312-异步)    

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

  #### 缩进
  #####  使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。     
  
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

  #### 空格
  ##### 以下几种情况不需要空格
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
  
  
  



  
