# aisjtu.github.io
上海交通大学AI专业（本科）课程信息



## 简介

更多信息可见：https://aisjtu.github.io

Resource 文件夹中包含了网址中所涉及的笔记等资源，你可以直接在此处浏览或下载。

此外 docs 文件夹用于网站生成与渲染，方式是 GitHub 内置的 Jekyll 生成器。

## 特别说明

我使用了 Tom Johnson *et al.* 的 [documentation-theme-jekyll](https://github.com/tomjoht/documentation-theme-jekyll) 模版进行网页的制作，并对其作了如下的修改：

- 为了更好地适应中文字体，我修改了路径 `docs/css/` 中的 `customstyles.css` 文件。
- 我修改了 topnav 中 Search 框、搜索结果框的大小，以更好的适配中文。
- 我在路径 `docs/_includes` 中加入了 `pdf.html` 文件，调用该文件可以实现网页嵌入。
- 同上一条，我加入了 `download.html` 文件，可以简洁的插入“下载 Button”.
- 原模版中使用 [Commento](https://commento.io) 进行评论，我将其更改为了免费开源的的 [gitalk](https://github.com/gitalk/gitalk/)。换言之，我在 `docs/_includes` 中加入了 `gitalk.html` 文件。

该模版的版权：Google LLC

网站中的部分表格基于 [jQuery DataTables](https://www.datatables.net) 所做，支持搜索、排序和折叠等显示。

