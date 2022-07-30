<h1 align="center">
AI-SJTU Courses Website
</h1>
<p align="center">
上海交通大学 AI 专业（本科）课程信息网站
</p>
<p align="center">
  <a href='https://gitHub.com/aisjtu/aisjtu.github.io/graphs/contributors/'>
    <img src='https://img.shields.io/github/contributors-anon/aisjtu/aisjtu.github.io?style=flat&color=red' alt='Contributors'>
  </a>
  <a href="https://gitHub.com/aisjtu/aisjtu.github.io/stargazers">
    <img alt="Stars" src="https://img.shields.io/github/stars/aisjtu/aisjtu.github.io?style=flat&color=blue">
  </a>
  <a href="http://hits.dwyl.com/aisjtu/aisjtugithubio">
    <img alt="Hits" src="https://hits.dwyl.com/aisjtu/aisjtu.github.io.svg?style=flat">
  </a>
</p>

## 简介

上海交通大学人工智能专业设立于 2019 年，「专业之新」导致了培养计划较为独特。

因此，该网站旨在为今后人工智能专业的学生提供丰富的课程信息，比如：

1. 来自前几届同学的**课程评价**、**课程笔记**与**复习笔记**。
2. 该门课程是否值得选修？
3. 是否应该~~翘掉课程以~~自学？
4. 该类学科的知识体系是什么？

值得说明的是，不同人的学习方法不尽相同，我们希望该网站的创立能够帮助到后来者发现属于自己的学习方法（~~找到自己的交大 AI 专业生存指南~~）。

更多信息可见：https://aisjtu.github.io 或 [https://aisjtu.icu](https://aisjtu.icu)

`Resource` 文件夹中包含了网址中所涉及的笔记等资源，你可以直接在此处浏览或下载。此外 `docs` 文件夹用于网站生成与渲染，核心 Markdown 文件在 `docs/pages` 目录下。

<details style='padding: 10px; border-radius:5px 30px 30px 5px; border-style: solid; border-width: 1px;'>
  <summary>下载及本地编译</summary>
  <ol>
    <li>
      克隆该库：
      <pre>git clone https://github.com/aisjtu/aisjtu.github.io.git</pre>
    <li>
      移动到对应文件夹：
      <pre>cd aisjtu.github.io/docs</pre>
    </li>
    <li>
      渲染：
      <pre>bash run_server.sh</pre>
    </li>
    <li>
      在浏览器中输入终端输出的链接后，即可在本地进行实时预览
    </li>
  </ol>
</details>

## 致谢

建立该网站的灵感来自于上海交通大学 IEEE 专业课程网站：[ieee.icu](https://ieee.icu/#/).

感谢上海交通大学的所有相关任课教师及助教，因为我的课程笔记等资源或多或少总结自他们的课程及 slides.

感谢所有贡献者：[Contributors](https://gitHub.com/aisjtu/aisjtu.github.io/graphs/contributors/)；感谢所有为该网站建立提供建议的朋友们。

网站中的部分表格基于 [jQuery DataTables](https://www.datatables.net) 所做，支持搜索、排序和折叠等显示；评论模块使用了开源的 [gitalk](https://github.com/gitalk/gitalk/) 库。

**特别的**，我使用了 Tom Johnson *et al.* 的 [documentation-theme-jekyll](https://github.com/tomjoht/documentation-theme-jekyll) 模版进行网页的制作，并对其作了如下的修改：

<details style='padding: 10px; border-radius:5px 30px 30px 5px; border-style: solid; border-width: 1px;'>
  <summary>相关改动</summary>
  <ol>
    <li>
      为了更好地适应中文字体，修改了路径 <code>docs/css/</code> 中的 <code>customstyles.css</code> 文件。
    <li>
      修改了 <code>topnav</code> 中 Search 框、搜索结果框的大小，以更好的适配中文。
    </li>
    <li>
      在路径 <code>docs/_includes</code> 中加入了 <code>pdf.html</code> 文件，调用该文件可以实现网页嵌入。
    </li>
    <li>
      同上一条，加入了 <code>download.html</code> 文件，可以简洁的插入“下载 Button”.
    </li>
    <li>
      原模版中使用 <a href="https://commento.io">Commento</a> 进行评论，我们将其更改为了免费开源的的 <a href="https://github.com/gitalk/gitalk/">gitalk</a>。换言之，在 <code>docs/_includes</code> 中加入了 <code>gitalk.html</code> 文件。
    </li>
    <li>
      在 <a href="https://github.com/Bluixe?tab=repositories">@Bluxie</a> 的帮助下，我优化了手机版 (@media) 下的搜索框，修改了 <code>customstyles.css</code> 文件中 “navbar breakpoint so that it converts to hamburger earlier” 部分。
    </li>
  </ol>
</details>

该模版的版权：**Google LLC**

