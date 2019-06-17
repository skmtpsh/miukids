# MIUKIDS

### miuKids 是关于孩子教育的网站。

[参考1] (http://www.17sucai.com/preview/1527619/2019-05-09/insure/index.html)
[参考2] (http://www.17sucai.com/preview/1527619/2019-05-10/home/index.html) 

## MarkDown 写法

# 1.以#开头，会转换为html的h1~h6标签，配合()可以做页面锚点导航
H1: 
# Header 1
H2: 
## Header 2
H3: 
### Header 3
H4: 
#### Header 4
H5: 
##### Header 5
H6: 
###### Header 6

# 2. 斜体、粗体、加粗斜体、删除线

*斜体*
**粗体**
***加粗斜体***

# 3.引用

> 引用了某人的一句话
>> 两层嵌套
>>> 多层嵌套

# 4.列表
1. 无序列表使用*-+后接文字，注意-后需要添加一个空格，列表可逐级嵌套，在前面加空格即可
+ 吃饭
  * 吃早饭
+ 吃饭
  + 吃早饭
+ 吃饭
 - 吃早饭
- 睡觉
- 打豆豆
* 打boss
2.有序列表直接使用数字和点
1.吃饭
2.睡觉
3.打豆豆


# 5.外链 

使用 [描述](链接地址) 为文字增加外链接。

[逄淑海](http://www.pangshuhai.com)

# 6.图片
![图片alt](图片地址 ''图片title'')
图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

![你好，我是谢耳朵](https://pic.cnblogs.com/avatar/1324387/20180124154851.png "谢耳朵")

# 7.分割线
三个或三个以上的---或***都可以做页面分割线，注意在分割线上方留一个回车
------

***

******

------***

------
# 8.表格

姓名|技能|排行
-| :-: | -:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟


# 9.行内代码块以及代码块
行内代码块
我是`行内代码块`呀
在文字前敲4个空格，即可实现简单的代码块
    代码块
 也可以使用三个`包含代码，实现。在第一段后接上编程语言名称可实现不同编程语言样式变化
(```)
function love(you) {
    if (!you) {
        return false;
    }
}
(```)
四. Markdown的高阶使用
1.目录锚点
在段落中填写[TOC] 以显示全文内容的目录结构。

2.todo列表

[ ] Cmd Markdown 开发
[ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
[ ] 支持以 PDF 格式导出文稿
[x] 新增Todo列表功能 语法参考
[x] 改进 LaTex 功能
[x] 修复 LaTex 公式渲染问题
[x] 新增 LaTex 公式编号功能 语法参考

MathJax: 让前端支持数学公式

[ ] 七月旅行准备
[ ] 准备邮轮上需要携带的物品
[ ] 浏览日本免税店的物品
[x] 购买蓝宝石公主号七月一日的船票


<math xmlns="http://www.w3.org/1998/Math/MathML"> 
  <mrow> 
    <mrow> 
      <msup> <mi>a</mi> <mn>2</mn> </msup> 
      <mo>+</mo> 
      <msup> <mi>b</mi> <mn>2</mn> </msup>
    </mrow> 
    <mo>=</mo> 
    <msup> <mi>c</mi> <mn>2</mn> </msup>
 </mrow> 
</math>
```
>// 结果
a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup>

但是它又一个致命问题，就是兼容性非常低，IE 和 Chrome 都不支持。
[MathML更多信息请参照这里](https://developer.mozilla.org/en-US/docs/Web/MathML/Element/math)

### 3、第三方库渲染
这个是比较靠谱的。在自己公司没有足够的开发资源的时候，使用第三方库来解决这方面的问题，还是很值得推荐的。
本文将要描述的是使用 **MathJax** 来解决公式渲染的问题。

## 二、MathJax 公式渲染

![mathjax.png](http://upload-images.jianshu.io/upload_images/2139239-aee39e5db64faa7a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用之前，我们来看一下它是什么：
```
Beautiful math in all browsers
A JavaScript display engine for mathematics that works in all browsers. 
No more setup for readers. It just works.
```
这个是它官网的简单介绍，简单的说，就是渲染公式的 js 库。
在使用之前，我们最好还需要掌握一些前置知识。我见过不少编辑公式的人都不动这个，这是使用 word 图形化工具去编写公式，其实这样效率还是蛮低的。

### LaTex

【百度百科】LaTeX（LATEX，音译“拉泰赫”）是一种基于ΤΕ
Χ的排版系统，由美国计算机学家莱斯利·[兰伯特](http://baike.baidu.com/subview/87545/15322469.htm)（Leslie Lamport）在20世纪80年代初期开发，利用这种格式，即使使用者没有排版和程序设计的知识也可以充分发挥由TeX所提供的强大功能，能在几天，甚至几小时内生成很多具有书籍质量的印刷品。

可以看到，编辑公式只是 latex 牛刀小试。而 mathjax 是支持 latex 排版的。

### MathJax 使用

mathjax使用主要有两种方式：
一种是引用 mathjax 的 js 库，然后再客户端渲染；
```
// mathjax js引用方式
<script type="text/javascript">
    window.MathJax = {
        showProcessingMessages: false,
        messageStyle: "none",
        tex2jax: {
            inlineMath: [['$', '$'], ["\\(", "\\)"]],
            processEscapes: true
        },
        "fast-preview": {disabled: true},
        CommonHTML: { linebreaks: { automatic: true } },
        "HTML-CSS": { linebreaks: { automatic: true } },
        SVG: { linebreaks: { automatic: true } },
        TeX: { noErrors: { disabled: true } },
        MathMenu: {
            styles: {
                ".MathJax_Menu": {"z-index":2001}
            }
        },
        AuthorInit: function () {
            MathJax.Hub.Register.StartupHook("MathMenu Ready",function () {MathJax.Menu.BGSTYLE["z-index"] = 2000;});
            MathJax.Hub.processSectionDelay = 0;
        }
    }
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-MML-AM_CHTML-full"></script>
```
另一种是部署 nodejs 的mathjax 服务，由 node 根据公式生成图片，再向前端返回图片地址。  
如何部署 mathjax node 服务，请点击这里：[MathJax_node](https://github.com/mathjax/MathJax-node)。

#### 两种方式的优缺点：
##### 引用js库
优点： 简单，方便
缺点：引用的 mathjax 库资源较多，在渲染的过程中，可能会出现公式抖动（公式的样式会一直在变化）
#### node 服务（推荐）
优点：将公式直接生成图片，稳定，方便，兼容性强
缺点：node 服务可能不稳定，对node需要有一定了解。
