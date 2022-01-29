---
title: Workflow maps
keywords: release notes, announcements, what's new, new features
sidebar: mydoc_sidebar
permalink: mydoc_format_req.html
folder: mydoc
---

{{site.data.alerts.callout_primary}}
<p>一位严谨的作家在写每一句话的时候，会至少问自己四个问题：我想说什么？用什么词来表达？什么样的形象或习语能让意思更清晰？这个形象的新鲜度够不够产生效果 ？</p>
<p align="right">—— 乔治奥威尔《政治与英语》</p>
{{site.data.alerts.end}}









## 拓展功能

关于更多细节：可查阅 [https://idratherbewriting.com/documentation-theme-jekyll/mydoc_adding_tooltips.html](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_adding_tooltips.html).

### 预览PDF文件

1. 将文件添加至 `/docs/Rsr_pdf/文件夹/文件名.pdf` 中。此处我们假设文件夹为“21”，文件名是“线性优化凸优化”。
1. 在 Markdown 文件中的对应位置添加如下代码[^1]：你可以调节 height 以控制高度。


```html
<embed src="https://anyeZHY.github.io/ai-sjtu.github.io/Rsr_pdf/21/线性优化凸优化.pdf" type="application/pdf" width="100%" height="250px"/>
```

最终效果如下

<embed src="https://anyeZHY.github.io/ai-sjtu.github.io/Rsr_pdf/21/线性优化凸优化.pdf" type="application/pdf" width="100%" height="250px"/>

### 添加下载按钮





## References

[^1]: https://stackoverflow.com/questions/30745981/opening-pdf-in-a-browser-with-github-pages


{% include links.html %}