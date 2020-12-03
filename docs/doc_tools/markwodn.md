# 语法

## 标题

一个#是一级标题，二个#是二级标题，以此类推。支持六级标题。

注：标准语法一般在#后跟个空格再写文字，貌似简书不加空格也行。

### 标题居中，并且放大

对于一级标题用 # 即可，但是有时候 我们需要居中，直接写是不行的

<center> 实习总结报告</center>

效果如下，这样虽然可以居中，但是markdown语法就没有效果了

由于markdown是兼容html的，我们可以这样

<center ><font size='70'>实习总结报告</font></center>


## 字体

    加粗:要加粗的文字左右分别用两个*号包起来

    斜体:要倾斜的文字左右分别用一个*号包起来

    斜体加粗:要倾斜和加粗的文字左右分别用三个*号包起来

    删除线:要加删除线的文字左右分别用两个~~号包起来

## 文字居中和带颜色

<center>这一行需要居中</center>

<font face="黑体" size=10>我是黑体字</font>

<font color=red size=22>颜色</font>

[markdown让文字居中和带颜色](https://www.cnblogs.com/bigmagic/p/3301b25e8b0b8ef8b9415379385a798c.html)


## 引用

    在引用的文字前加>即可。引用也可以嵌套，如加两个>>三个>>>
    n个...    貌似可以一直加下去，但没神马卵用

## 分割线

    三个或者三个以上的 - 或者 * 都可以。

## 图片

![图片alt](图片地址 ''图片title'')

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

### 

<div align=center>![这里写图片描述](http:...) 

[Markdown-图片设置（大小，居中）](https://blog.csdn.net/qq_35451572/article/details/79443467)

<div align=left>

## 超链接

语法：

[超链接名](超链接地址 "超链接title")
title可加可不加

## 列表

* 无序列表

语法：
无序列表用 - + * 任何一种都可以

- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格

* 有序列表

语法：
数字加点

1.列表内容
2.列表内容
3.列表内容

注意：序号跟内容之间要有空格


* 列表嵌套

上一级和下一级之间敲三个空格即可

## 表格

语法：
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略

## 代码

语法：
单行代码：代码之间分别用一个反引号包起来
    `代码内容`

代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行
```
  代码...
  代码...
  代码...
```

## 流程图

<div align=center>
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op

```

<div align=left>

# 工具

## Markdown Preview Enhanced
Markdown Preview Enhanced 是一款为 Atom 以及 Visual Studio Code 编辑器编写的超级强大的 Markdown 插件。 这款插件意在让你拥有飘逸的 Markdown 写作体验。

[Markdown Preview Enhanced](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)

[src](https://github.com/shd101wyy/vscode-markdown-preview-enhanced)

[Powerful markdown tool ](https://github.com/shd101wyy/mume)

[markdown preview enhanced文档（简体中文版）](https://www.bookstack.cn/read/mpe/zh-cn-_sidebar.md)

[关于插件Markdown Preview Enhanced的使用技巧](https://blog.csdn.net/weixin_34407348/article/details/94321593?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)
