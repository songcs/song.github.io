---
title: hexo学习笔记
date: 2019-03-15 23:18:16
tags: 
- hexo
---
# 创建分类

## 生成“分类”页并添加tpye属性
打开命令行，进入博客所在文件夹。执行命令
```shell
$ hexo new page categories
```
成功后会提示：

```shell
INFO  Created: ~/Documents/blog/source/categories/index.md
```
根据上面的路径，找到index.md这个文件，打开后默认内容是这样的：
添加type: "categories"到内容中，添加后是这样的：
```shell
---
title: 文章分类
date: 2017-05-27 13:47:40
type: "categories"
---
```
保存并关闭文件。

## 给文章添加“categories”属性
打开需要添加分类的文章，为其添加`categories`属性。下方的`categories`: web前端表示添加这篇文章到“web前端”这个分类。注意：hexo一篇文章只能属于一个分类，也就是说如果在“- web前端”下方添加“-xxx”，hexo不会产生两个分类，而是把分类嵌套（**即该文章属于** “- web前端”下的 “-xxx ”分类）。
```shell
---
title: jQuery对表单的操作及更多应用
date: 2017-05-26 12:12:57
categories: 
- web前端
---
```
至此，成功给文章添加分类，点击首页的“分类”可以看到该分类下的所有文章。当然，只有添加了categories: xxx的文章才会被收录到首页的“分类”中。


# 创建标签
## 生成“标签”页并添加tpye属性
打开命令行，进入博客所在文件夹。执行命令
```shell
$ hexo new page tags
```
成功后会提示：
```shell
INFO  Created: ~/Documents/blog/source/tags/index.md
```
根据上面的路径，找到index.md这个文件，打开后默认内容是这样的：
```shell
---
title: 标签
date: 2017-05-27 14:22:08
---
```
添加type: `tags`到内容中，添加后是这样的：
```shell
---
title: 文章分类
date: 2017-05-27 13:47:40
type: "tags"
---
```
保存并关闭文件。

## 给文章添加`tags`属性
打开需要添加标签的文章，为其添加tags属性。下方的tags:下方的- jQuery - 表格
- 表单验证就是这篇文章的标签了
```shell
---
title: jQuery对表单的操作及更多应用
date: 2017-05-26 12:12:57
categories: 
- web前端
tags:
- jQuery
- 表格
- 表单验证
---
```
至此，成功给文章添加分类，点击首页的“标签”可以看到该标签下的所有文章。当然，只有添加了tags: xxx的文章才会被收录到首页的“标签”中。

细心的朋友可能已经发现，这两个的设置几乎一模一样！是的，没错，思路都是一样的。所以我们可以打开scaffolds/post.md文件，在`tages:`上面加入`categories:`,保存后，之后执行hexo new 文章名命令生成的文件，页面里就有`categories:`项了。

`scaffolds`目录下，是新建页面的模板，执行新建命令时，是根据这里的模板页来完成的，所以可以在这里根据你自己的需求添加一些默认值。

# 并列分类
## 并列分类
```shell
categories:
- [Linux]
- [Tools]
```
```md
categories:
- [Linux, Hexo]
- [Tools, PHP]
```
# 标签插件
> https://hexo.io/zh-cn/docs/tag-plugins

## 引用块
在文章中插入引言，可包含作者、来源和标题。

**别号**： quote
```
{% blockquote [author[, source]] [link] [source_link_title] %}
content
{% endblockquote %}
```
样例
没有提供参数，则只输出普通的 blockquote
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
引用书上的句子
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

引用 Twitter
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

引用网络上的文章
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

## 代码块
在文章中插入代码。

**别名**： code
```
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```
样例
普通的代码块
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}

指定语言
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

附加说明
```
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
```
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
附加说明和网址
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}

反引号代码块
另一种形式的代码块，不同的是它使用三个反引号来包裹。
```
\`\`\` [language] [title] [url] [link text] code snippet \`\`\`
```
## Pull Quote
在文章中插入 Pull quote。
```
{% pullquote [class] %}
content
{% endpullquote %}
```
## jsFiddle
在文章中嵌入 jsFiddle。
```
{% jsfiddle shorttag [tabs] [skin] [width] [height] %}
```
## Gist
在文章中嵌入 Gist。
```
{% gist gist_id [filename] %}
```
## iframe
在文章中插入 iframe。
```
{% iframe url [width] [height] %}
```
## Image
在文章中插入指定大小的图片。
```
{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```
## Link
在文章中插入链接，并自动给外部链接添加 target="_blank" 属性。
```
{% link text url [external] [title] %}
```
## Include Code
插入 source 文件夹内的代码文件。
```
{% include_code [title] [lang:language] path/to/file %}
```
## Youtube
在文章中插入 Youtube 视频。
```
{% youtube video_id %}
```
## Vimeo
在文章中插入 Vimeo 视频。
```
{% vimeo video_id %}
```
## 引用文章
引用其他文章的链接。
```
{% post_path slug %}
{% post_link slug [title] %}
```
## 引用资源
引用文章的资源。
```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```
## Raw
如果您想在文章中插入 Swig 标签，可以尝试使用 Raw 标签，以免发生解析异常。
```
{% raw %}
content
{% endraw %}
```
# 资源文件夹

资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在 `source/images` 文件夹中。然后通过类似于 `![](/images/image.jpg)` 的方法访问它们。

## 文章资源文件夹
对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo也提供了更组织化的方式来管理资源。这个稍微有些复杂但是管理资源非常方便的功能可以通过将 `config.yml` 文件中的 `post_asset_folder` 选项设为 `true` 来打开。
{% codeblock _config.yml lang:yml %}
post_asset_folder: true
{% endcodeblock %}
当资源文件管理功能打开后，Hexo将会在你每一次通过 hexo new `[layout] <title>` 命令创建新文章时自动创建一个文件夹。这个资源文件夹将会有与这个 markdown 文件一样的名字。将所有与你的文章有关的资源放在这个关联文件夹中之后，你可以通过相对路径来引用它们，这样你就得到了一个更简单而且方便得多的工作流。

## 相对路径引用的标签插件
```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```

比如说：当你打开文章资源文件夹功能后，你把一个 `example.jpg` 图片放在了你的资源文件夹中，如果通过使用相对路径的常规 markdown 语法 `![](/example.jpg)` ，它将 不会 出现在首页上。（但是它会在文章中按你期待的方式工作
正确的引用图片方式是使用下列的标签插件而不是 markdown ：
```
{% asset_img example.jpg This is an example image %}
```

# 公式设置
## next主题内解析数学公式（主页内不解析）
{% codeblock next/_config.yml lang:bash %}
# MathJax Support
mathjax:
  enable: true
  per_page: true
{% endcodeblock %}
还需要在文章的Front-matter里打开mathjax开关，如下：
{% codeblock next/_config.yml %}
# MathJax Support
---
title: index.html
date: 2016-12-28 21:01:30
tags:
mathjax: true
--
{% endcodeblock %}
## 主页内解析
{% codeblock hexo/_config.yml lang:bash %}
$ npm install hexo-math --save
{% endcodeblock %}
在站点配置文件 _config.yml 中添加：
{% codeblock hexo/_config.yml lang:bash %}
math:
  engine: 'mathjax' # or 'katex'
  mathjax:
    # src: custom_mathjax_source
    config:
      # MathJax config
{% endcodeblock %}
{% codeblock %}
$数学公式$ 行内 不独占一行
$$数学公式$$ 行间 独占一行
{% endcodeblock %}