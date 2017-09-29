# 笔记

## 09/26

### 1. `ie=edge`表示强制以最新的IE浏览器模式渲染页面。

```html
<meta http-equiv="X-UA-Compatible" content="ie=edge">
```

### 2. 关于IE浏览器支持

```html
<!--[if lte IE8]>
    <P>浏览器版本过低！！！</p>
<![endif]-->    
```

这段代码，表示，低于IE8版本的浏览器，将显示p元素的内容。

这个结构为ie的选择判断结构。

```html
<!--[if gt/lt/gte/lte IE8]>

<![endif]-->   
```

|`gt`|`lt`|`gte`|`lte`|
|:-----:|:-----:|:-----:|:-----:|
|版本高于IE8|版本低于IE8|版本大于等于IE8|版本小于等于IE8|


## 09/28

### 1. `px,em,rem`

1. `em`


    1. `em`相对参照物为父元素的`font-size`

    2. `em`具有继承的特点

    3. 当未设置`font-size`时，浏览器会有一个默认的em的设置：`1em = 16px`

    *缺点：容易混乱*


2. `rem`

    1. `rem`的*相对参照物为根元素html*，相于参照固定不变所以比较好计算。
    2. 当为设置`font-size`时，浏览器会有一个默认的rem设置：`1rem = 16px`。
    
    *CSS3新特性，IE9以下版本不支持该属性。解决该问题的方法如下：*

    ```css
    font-size: 16px;
    font-size: 1rem;
    ```

    上述代码即可解决IE9以下版本不兼容rem的问题。

    ***根元素`<html>`中定义了一个基本字体大小为62.5%（也就是10px。设置这个值主要方便计算 ）***

### 2. 清除浮动

1. 元素末尾增加一个div清除浮动

2. overflow

3. 给父元素清除浮动

4. 伪类清除浮动

```css
.clearfix::after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}

.clearfix {
    zoom: 1;
}
```

`BFC` 块级格式化上下文
只要触发了BFC就能触发清除浮动，
怎么触发BFC, 如float，overflow。（此处有待深究）

创建匿名表格但愿触发BFC

```css
.clearfix::before,
.clearfix::after {
    content: " ";
    display: table;
}

.clearfix::after {
    clear: both;
}

.clearfix {
    *zoom: 1;
}
```



## 09/29

### 1. Chrome 中文字体最小下限是12px

因此当`html`的`font-size`设置为62.5%的时候，实际在Chrome中中文不是10px，而是12px。

因此3rem就是36px


### 2. `li`设置导航时，两个元素中间有分割线。

```css
header .top ul li + li {
    border-left: 1px solid #999999;
    margin-left: -3px;
}
```
当设置`display: inline-block`的时候，*元素中间会存在间隙*，本质是html元素中间的空白字符（如：换行符）。

解决方法：
    1. ul（父元素）的`font-size`设置为0，再给li设置`font-size`。
    2. 手动清除空白符。
    3. `margin-left: -3px`设置副边距;
    4. css3解决方案white-space-collapsing(兼容性不好)


### 3. css3计算方法 `calc()`

```css
element{
 width: calc(33.3333333333% - 3rem);
}
```
三等分宽度


### 4. `@media only screen and (max-width: 80rem){}`

媒体查询使用相对单位的时候会有一个坑，尽管设置了html的`1rem = 10px`，但是媒体查询级别很高，并非html的一个子元素，直接应用到最高级别，为浏览器的默认值。即`1rem = 16px`

因为本身为浏览器默认值，rem存在兼容性问题，所以建议使用em

`@media only screen and (max-width: 50em){}`

### 5. `@media print {}`添加打印样式