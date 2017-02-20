
source:

# CSS 书写规范

## 外部CSS引用

必须使用如下格式( rel 在前，href 在后，无 type="text/css" 及 charset )：

```css
<link rel="stylesheet" href="http://pic.lvmama.com/styles/v3/combo.css" >
```

## CSS 注意事项

- 无特殊说明，编码统一为utf-8；
- 防止文件合并及编码转换时造成问题，请将样式中文字体名字改成对应的英文名字（unicode码），如：宋体（ \5b8b\4f53）微软雅黑（”Microsoft YaHei”,”\5FAE\8F6F\96C5\9ED1″）；
- 书写代码前，考虑并提高样式重复使用率；
- 禁止使用 expression 表达式；
- 禁止滥用 `!important`；
- 能缩写的尽量缩写，如 `padding:5px 0 0 5px;`；
- 层级(z-index)必须清晰明确，适当划分组件层级范围，禁止层级间盲目攀比；
- 为方便组件模块化和提高弹性，正常情况下，为避免外边界冲突，组件不应设置外边界，外边界用组合css方式实现，如：m10{margin:10px}mt10{margin-top:10px}等；
- 必须为大区块&重要模块的样式添加注释，小区块适量注释；
- 正式发布前应进行压缩，压缩后文件的命名应添加 '.min' 后缀；
- 代码缩进与格式：请参照以下 CSS 书写规范；

## CSS 书写规范

以下书写规范针对组件开发使用，非组件书写格式建议使用单行式排版。

- 使用四个空格的 soft-tabs 缩进
- 写组选择器时，保持选择器各占一行
- 在属性块的左 '{' 前应该有一个空格
- 关闭属性块的右 '}' 要新起一行
- 每个属性的 ':' 后包含一个空格
- 每个属性应该自己独占一行
- 分割选择器的 ',' 后应该包含一个空格
- Don't include spaces after commas in RGB or RGBa colors, and don't preface values with a leading zero
- 小写所有16进制值, 例如, `#fff` 而非 `#FFF`
- 使用简写16进制值, 例如, `#fff` 而非 `#ffffff`
- 选择器中引用属性值, 例如, `input[type="text"]`
- 避免0值设置单位, 例如, `margin: 0;` 而非 `margin: 0px;`

## 为方便调试，css底部必须书写此css名称以及功能描述，如下：

```css
/*
 @名称: channel.css
 @功能: 各大频道页样式 //注意适当的隔行划分
 */

/* 频道全局样式 */
.col-w { width: 780px; float: right;}
.aside { width: 200px; float: left;}


/* 频道侧边栏 */
.side-box { margin-bottom: 15px;}


/* 频道主内容区域 */
.ctitle { }


/* 特色酒店 */
.pro-search { }


/* 火车票 */
.ticket-search { }
```

多个 class 同时定义，多行书写

```css
// bad
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

// good
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

常见的CSS术语，请参见 [syntax section of the Cascading Style Sheets article](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) on Wikipedia。

## 属性顺序

```css
.declaration-order {
  /* Positioning 定位 */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model 盒模型 */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography 排版 */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5
  color: #333;
  text-align: center;

  /* Visual 视觉 */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc 其他 */
  opacity: 1;
}
```

相关属性应放在一起，将定位与盒模型属性写在最前面，其次是排版和视觉效果的属性。

关于属性顺序的完整列表，请参考 [Recess](http://twitter.github.com/recess)。

## 格式化例外

某些情况下，这是有道理的，稍微偏离默认的 [语法](#css-syntax)。

## 前缀属性

当使用供应商前缀的属性时，每个属性缩进到vlaue值垂直对齐的位置，方便多行编辑。

```css
/* Corner radius-圆角 */
.selector {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
```

注：`-khtml-border-radius: 3px;` 是苹果的那个浏览器的，现在使用 `-webkit-`。

在 Textmate、Sublime Text 2 以及 notepad++等工具中, 都支持多行编辑。

NOTE: 目前编辑器推荐选用 Atom 以及 VSCode。并且不再书写浏览器前缀，可以在编译打包过程通过 autoprefixer 自动处理。

## 单一属性的书写规则

在有些情况下，每个样式只有一个属性，考虑到可读性及更快地编辑删除等，保持同一行书写。

```css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

## 可读性

代码是由人来书写和维护的。确保你的代码有很好的注释描述，以便他人使用。

## 注释

好的代码都有一个良好的代码注释而不仅仅是一个类名

```css
// bad
/* Modal header */
.modal-header {
  ...
}

// good
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

## 类名与命名

- 保持类名使用小写字母或连接符 (不要使用下划线或驼峰命名法)
- 避免使用随意的首字符命名法
- 保持命名尽可能短并简洁
- 使用有意义的命名；使用结构化或目的性的意义名称
- 根据最近的父组件基类作为命名前缀
- (废弃)为JavaScript预留钩子的命名，请以 JS_ 起始，比如：JS_ui-tab, JS_slidebox；或者使用 data-* 挂钩JS功能

```css
// bad
.t { ... }
.red { ... }
.header { ... }

// good
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

## 选择器

- 在通用的元素标签中使用类
- 要保持尽量简短，并限制每个选择器最多三个class
- 必要时使用最近的父类 (如，在不使用前缀类时)

```css
// bad
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

// good
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

## 组织

- 组织代码段的组成部分
- 指定一个一致的注释层次结构
- 如果使用多个css文件，则按组件进行划分

更多详情常见：CSS目录下 readme.md 文件
