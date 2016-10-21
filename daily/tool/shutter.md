# shutter

tags:截图

shutter 是 linux 下非常好用的一款截图软件，功能强大。

> 注： shutter是快门的意思。

## 安装

可以通过软件管理器直接安装，"开始菜单" -> "系统管理" -> "软件管理器"，搜索 `shutter`：

![](images/shutter_search.jpg)

点击安装即可。

## 配套软件

需要安装几个配套的软件，才能使用 shutter 全面的功能:

- gnome-web-photo: a tool to generate full-size image files and thumbnails from HTML files and web pages 用于抓取整个网页
- libgoo-canvas-perl: canvas widget 用于编辑抓图文件,增加标注等，这个必须安装，不然非常的不方便，截图之后加个箭头写个标注是常见的事。

## 设置

### 图片导出格式

打开 shutter，菜单中点 "编辑" -> "Preference" 打开 首选项，点"主要"。

图片格式中，默认时png格式，文件大小会稍微嫌大，可以设置为 jpg 格式，然后图片质量设置为 80%.

