---
title: Pull Request 贡献指南
sidebar: mydoc_sidebar
permalink: mydoc_format_req.html
folder: mydoc
---

{{site.data.alerts.callout_primary}}
<p>一位严谨的作家在写每一句话的时候，会至少问自己四个问题：我想说什么？用什么词来表达？什么样的形象或习语能让意思更清晰？这个形象的新鲜度够不够产生效果 ？</p>
<p align="right">—— 乔治奥威尔《政治与英语》</p>
{{site.data.alerts.end}}

## 贡献流程说明

### 修改文件

找到对应文件直接进行修改即可，推荐通过 *Edit me* 按钮进行定位，通常而言 Markdown 格式文档位于路径`docs/pages/`下。

与此同时，你可以选择在“课程总览”的表格中找到对应课程，添加或修改其信息。

### 新建文件

需要进行如下几个步骤：

1. 在 `Resource/useful_files/` 中找到 Markdown 格式的初始模版，在其基础上建立你的课程评价。
2. 将上述 Markdown 文件置于 `docs/pages/` 的文件夹中，规则：大一上课程--11，大一下课程--12，大二上课程--21，以此类推。
3. 在 `docs/_data/sidebars` 找到对应的yml文件（规则同2），在其中添加该课程。
4. 在 `docs/pages/mydoc/` 中找到对应的“课程总览”文件（名称为 `mydoc_ij.md`，规则同2），在表格中添加该课程。

步骤较为繁琐，如有问题可以与我联系。

### 如何判断网络正常渲染？

可以检查当前 [Environments](https://github.com/aisjtu/aisjtu.github.io/deployments) 状态是否为 Active, 若为 Failure 则说明 Jekyll 渲染失败。

### 一些不推荐的做法

- 对课程负面评价
- 分享电子版教材（应当注意版权）
- 分享老师的 PPT 或 Lecture Notes（应得到老师的许可）




## 拓展功能

我使用了 Tom Johnson *et al.* 制作的 [documentation-theme-jekyll](https://github.com/tomjoht/documentation-theme-jekyll) 模版，因此关于更多实施细节：可查阅网站 [https://idratherbewriting.com/documentation-theme-jekyll/mydoc_adding_tooltips.html](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_adding_tooltips.html) 中 Formatting 下的多个 subsections. **当然，我会在本节中简明地介绍他们的用法。**

同时基于一些基本的html知识，我也会在本小节中给出一些**额外的拓展功能的实现方法**。

当你遇到问题时，我推荐你点开本页的「Edit me」直接查看其源代码格式, which is **Intriguing**.

Remark: the References Part may be **practical**.

### 预览PDF文件[^1]

1. 将文件添加至 `/docs/Rsr_pdf` 中。此处我们假设文件是`IQM.pdf`。
1. 在 Markdown 文件中的对应位置添加如下代码：你可以调节 height 以控制高度。


```html
{% raw %}{% include pdf.html src="https://aisjtu.github.io/Rsr_pdf/IQM.pdf" %}{% endraw %}
```

最终效果如下

{% include pdf.html src="https://aisjtu.github.io/Rsr_pdf/IQM.pdf"%}

### 添加下载按钮

假设你的下载链接为「https://github.com/aisjtu/path/file.pdf」，则代码为：

```html
{% raw %}{% include download.html href="https://github.com/aisjtu/path/file.pdf" type="PDF"%}{% endraw %}
```

效果如下：

{% include download.html href="https://github.com/aisjtu/path/file.pdf" type="PDF"%}

### 添加色彩标签[^2]

```html
<span class="label label-default">Default 此处你可以更改（下同）</span>
<span class="label label-primary">Primary</span>
<span class="label label-success">Success</span>
<span class="label label-info">Info</span>
<span class="label label-warning">Warning</span>
<span class="label label-danger">Danger</span>
```

<span class="label label-default">Defaul 此处你可以更改（下同）</span>
<span class="label label-primary">Primary</span>
<span class="label label-success">Success</span>
<span class="label label-info">Info</span>
<span class="label label-warning">Warning</span>
<span class="label label-danger">Danger</span>

### 添加色彩着重引用[^3]

```html
{% raw %}{% include callout.html content="This is my **danger** type callout. It has a border on the left whose color you define by passing a type parameter." type="danger" %}{% endraw %}
```

你可以更改 type 来改变左侧着色：

{% include callout.html content="This is my **danger** type callout. It has a border on the left whose color you define by passing a type parameter." type="danger" %}

{% include callout.html content="This is my **default** type callout. It has a border on the left whose color you define by passing a type parameter." type="default" %}

{% include callout.html content="This is my **primary** type callout. It has a border on the left whose color you define by passing a type parameter." type="primary" %}

{% include callout.html content="This is my **success** type callout. It has a border on the left whose color you define by passing a type parameter." type="success" %}

{% include callout.html content="This is my **info** type callout. It has a border on the left whose color you define by passing a type parameter." type="info" %}

{% include callout.html content="This is my **warning** type callout. It has a border on the left whose color you define by passing a type parameter." type="warning" %}

content 中内容并不支持 Markdown 格式，你需要用 `<br></br>` 以进行换行操作。

更 Robust 的做法是：

```html
{% raw %}{{site.data.alerts.callout_primary}}
<p>你可以更改上方的 primary 以选取不同颜色</p>
<p align="center">在这里你可以充分的发挥你的 html 相关操作</p>
<pre>
def func(x): 
	# You could define a function here
	return x+1
</pre>
{{site.data.alerts.end}}{% endraw %}
```

{{site.data.alerts.callout_primary}}
<p>你可以更改上方的 primary 以选取不同颜色</p>
<p align="center">在这里你可以充分的发挥你的 html 相关操作</p>
<pre>
def func(x):
	# You could define a function here
	return x+1
</pre>

{{site.data.alerts.end}}


## References

[^1]: [https://stackoverflow.com/questions/30745981/opening-pdf-in-a-browser-with-github-pages](https://stackoverflow.com/questions/30745981/opening-pdf-in-a-browser-with-github-pages)
[^2]: [https://idratherbewriting.com/documentation-theme-jekyll/mydoc_labels.html](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_labels.html)
[^3]: [https://idratherbewriting.com/documentation-theme-jekyll/mydoc_alerts.html](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_alerts.html)

{% include links.html %}
