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


### 3. 