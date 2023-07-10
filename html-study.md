# Web前端（Html/CSS/JS）
1、html-超文本标记语言，页面结构，类似于人类的身体组织；
2、css-层叠样式表，审美、美化页面的样式，类似于人的穿衣打扮；
3、JS-页面的交互行为，类似于人体的动作、更有生命力。

## Html

今天用vs code新建了test.html- 输入html：5 生成了html的骨架，由四部分组成：
 1. **Doctype html/xhtml** ，用于告诉浏览器用html还是xhtml；
 2. **html lang="en/zh-CN"** ，用于告诉浏览器使用的语言，en为英文，Ch-CN为中文；
 3. **head.../head** ，为头部标签；
 5.  **body.../body**，为html页面主体显示的内容，包含页面标题title也在这里设置等；


## head.../head(头部标签，meta标签-表示“元”，表示基本配置项目)
 
  **meta...** ，用于为页面提供基本信息，例如：
 1. meta name="charset"  content=“UTF-8/gb2312”utf-8为字符量多，但速度相对gb2312较慢，除对网页速度有要求速度外，使用utf-8居多；
 2. meta name="keywords" （关键词）conent="..."（关键词内容）可用于提高搜索的命中率；
 3. meta name="descrition"（描述） conent="..."（描述内容）用于对该网页进行描述 ；
 4.  meta http-equiv="Content-Type" conent="..."指围绕什么内容类型 ；


## body.../body(身体标签，定义html显示的主体内容)
 可用link（打开默认的颜色）/alink（点击时显示的颜色）/vlink（点击后显示的颜色）对body标签内容进行颜色设定；
 1. p.../p,段落标签，可以用于将文档或网页分割为不同段落；
 2. title.../title,用于网页的命名；
 3. h1-h6,指对标题的字体大小进行定义，h1是定义最大标题，反着h6是定义最小标题 ；具有align属性，可定义标题的位置：left/center/right。
 4.  hr /-horizontal rule水平分割线，可用于文档或网页的分割线，起到视觉上的分割效果，结构更清晰可见；可用size（分割线的粗细数值）/width=500或width=70%（设定分割线的长短）可以是绝对值（单位是像素）或相对值，如果设置为相对值的话，内定为100%/color="..."(设定分割线的颜色)需要用颜色代码输入/noshade（分割线不需设阴影）表示为设定线条为平面显示，若没设定不需阴影的则表示分割线为立体，非平面视觉；
 5. br，用于文档中的字体分行，于p.../p的段落标签相比，br可直接用于内容中间，且无需结束符；
 6. div.../div（division“分割”）和span.../span（范围、跨度），都是用于分割标签中的内容为独立板块，但div分割后必须占据一行，而span虽然作用一致，但标签后内容不分行；
 7. left/center/right，用于定义内容位置的标签；
 8. pre.../pre，用来预设网页或文档的格式，将标签内所有的空白字符(空格、换行符)地输出结果（浏览器不可忽略空格和空行）
 9. 字体标签，用于内容需要显示的符号，如：nbsp（non-breaking spacing不断打空格）/lt小于号<（less than）/gt;：大于号>（greater than）等；字体格式也可设置，如：u.../u可对标签内容加下划线/s.../s或del.../del对标签内容加删除线等。
 10. 链接标签，base href="..."和a href="..."加网址或链接位置，表示为点击后可跳转至该页面，所有a href都是以base href为基准；
 11. 图片标签：img（image图像），表现为img src="..."(可以是本地图片或网络图片)，能插入图像类型为：jpg(jpeg)、gif、png、bmp等，网页中无法插入psd、ai等类型；其中可以用width和height对图像进行大小定义，alt可用文字形式对图像显示不了时替代其图像显示，title提示文本，表现为鼠标悬停在图像时会出现文本提示；
 12. 列表标签：
 （1）无序列表ul（unordered lis）可用type对ul定义属性值如：disc实心圆点/square实心方点/circle空心圆，且li也可用其定义属性；无序列表里的每一项li（list item列表项）-不可单独存在，须表现在ul里，反之ul的“儿子”只能是li，但是li是一个容器级标签，li里面什么都能放，甚至可以再放一个ul。
 （2）有序列表：ol（Ordered List）可用type对ol进行定义，如：阿拉伯数字1（默认）或a、A、i、I；也可用ul代替ol使用。
 （3）定义列表：dl（definition list无属性定义，子元素只能是dt和dd）可用于表现为dl里含有dt，dt里含有dd，一二三级形式表现出来。
 13. 表格标签：table表格-tr行-td单元格，表格是由每一行的单元格组成，且可对table进行定义，如：border（边框，单位为像素）等，也对单元格进行格式话定义，如：colspan="..."横向合并/rowspan="..."纵向合并,...中可填需要对几个单元格进行合并，或者加align对表格位置进行定义。
 14. **框架标签：frameset表现为一个网页有多个页面显示，里面用多个frame来定义，一个frame表现一个页面，不可放在body的标签里，body表示仅一个页面，frameset和body只能二选一。**
 15. iframe是body里面的子标签，可用于body里内嵌框架。
