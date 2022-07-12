---
title: TeX 使用指南
sidebar: mydoc_sidebar
permalink: others_how.html
folder: mydoc
---

{{site.data.alerts.callout_primary}}
<p>你给他留了一份，你的记忆。</p>
<p align="right">—— Freebird Games《影子工厂》</p>
{{site.data.alerts.end}}

## LaTeX 资源库

强烈建议在**大一上**时学会且在大一下熟练掌握 LaTeX 的使用，以下是我常用的一些资源及网站。

- Overleaf 在线编辑器：[https://overleaf.com](https://overleaf.com) 以及上海交通大学 TeX 在线编辑器：[https://latex.sjtu.edu.cn](https://latex.sjtu.edu.cn)
- LaTeX 编辑部：[https://www.latexstudio.net/hulatex/index.htm](https://www.latexstudio.net/hulatex/index.htm)，非常实用的中文教程，其中收录了大量的 package 及其使用说明。

- 「physics」宏包，极大化简公式环境，其源文件：[document](https://mirrors.tuna.tsinghua.edu.cn/CTAN/macros/latex/contrib/physics/physics.pdf)
- 常用的 LaTeX Mathematical Symbols：[https://www.caam.rice.edu/~heinken/latex/symbols.pdf](https://www.caam.rice.edu/~heinken/latex/symbols.pdf)
- Comprehensive TeX Archive Network 官网：[https://ctan.org](https://ctan.org)

我使用 [Vim](others_vim.html) 作 TeX 文件的编辑器，参考了如下教程：

- Gilles Castel's Blog: [https://castel.dev/post/lecture-notes-1/](https://castel.dev/post/lecture-notes-1/)
- xiaoronglv 博客：[https://ruby-china.org/topics/25023](https://ruby-china.org/topics/25023)

注：Vim+TeX 的使用会让你的写作效率翻倍，但是环境配置的难度稍大，大二上整个学期我都在对此作优化，你可以参考我的 GitHub Repository：[Vim-LaTeX-Configuration](https://github.com/anyeZHY/Vim-LaTeX-Configuration)

## 建立合理的文件树

```
Lecture-A
       ├── preamble.tex
       ├── ln_preamble.tex
       ├── Homework
       │   ├── HW1
       │   │   ├── HW1.tex
       │   │   └── HW1.pdf
       │   └── ...
       ├── LectureNotes
       │   ├── LectureNotes.tex
       │   ├── LectureNotes.pdf
       │   └── Notes
       │       ├── 1.tex
       │       ├── 2.tex
       │       └── ...
       └── slides
           └── ...
```

我的作业 TeX 文件中为：

```latex
\documentclass{article}
\input{path/Lecture-A/preamble}
\setstretch{1.45}
\begin{document}
\title{Homework 1}
\maketitle

这里是作业内容。

\end{document}
```

Lecture Notes 的 TeX 文件：

```latex
\documentclass{article}
\input{../preamble}
\input{../ln_preamble
% \graphicspath{{figures/}}

\begin{document}
\title{Introduction To Quantum Mechanics}
\maketitle
\tableofcontents
\newpage
\input{Notes/1}
\input{Notes/2}

\end{document}
```

## preamble.tex

```latex
%! Tex program = xelatex
% \documentclass{article}
%中文
%\usepackage[UTF8]{ctex}
%数学公式
\usepackage{amsmath,amssymb}
%\usepackage{ntheorem}
% \usepackage[framemethod=TikZ]{mdframed}
\usepackage{amsthm}
%边界
\usepackage[letterpaper,top=3cm,bottom=3cm,left=3cm,right=3cm,marginparwidth=1.75cm]{geometry}%table package
%Table
\usepackage{multirow,booktabs}
\usepackage{makecell}
%字体颜色
\usepackage{color}
\usepackage[dvipsnames]{xcolor}  % 更全的色系
%代码
\usepackage[OT1]{fontenc}
% MATLAB 代码风格
%\usepackage[framed,numbered,autolinebreaks,useliterate]{/Users/anye_zhenhaoyu/Desktop/Latex/mcode}
\usepackage{listings}
\usepackage{algorithm}
\usepackage{algorithmic}
\usepackage{pythonhighlight} % Python
%插图
\usepackage{graphicx}
%改变item格式
\usepackage{enumerate}
%物理
\usepackage{physics}
%extra arrows
\usepackage{extarrows}
% caption（居中指令）
%\usepackage[justification=centering]{caption}
\usepackage{caption}
% htpb
\usepackage{stfloats}
% pdf 拼接
\usepackage{pdfpages}
% 超链接url
\usepackage{url}
% \usepackage{tikz}
\usepackage{pgfplots}
\pgfplotsset{compat=newest}
\usepackage[colorlinks=true, allcolors=red]{hyperref}

% --------------definations-------------- %
\def\*#1{\boldsymbol{#1}}
\def\+#1{\mathcal{#1}} 
\def\-#1{\bar{#1}}
% Domains
\def\RR{\mathbb{R}}
\def\CC{\mathbb{C}}
\def\NN{\mathbb{N}}
\def\ZZ{\mathbb{Z}}
% Newcommand
\newcommand{\inner}[2]{\langle #1,#2\rangle} 
\newcommand{\numP}{\#\mathbf{P}} 
\renewcommand{\P}{\mathbf{P}}
\newcommand{\Var}[2][]{\mathbf{Var}_{#1}\left[#2\right]}
\newcommand{\E}[2][]{\mathbf{E}_{#1}\left[#2\right]}
\renewcommand{\emptyset}{\varnothing}
\newcommand{\ol}{\overline}
\newcommand{\argmin}{\mathop{\arg\min}}
\newcommand{\argmax}{\mathop{\arg\max}}
\renewcommand{\abs}[1]{\qty|#1|}
\newcommand{\defeq}{\triangleq} % triangle over =
\def\deq{\xlongequal{def}} % 'def' over =
\def\LHS{\text{LHS}}
\def\RHS{\text{RHS}}
\def\angbr#1{\langle#1\rangle} % <x>

\def\Esolve{\textcolor{blue}{Solve: }}
\def\Eproof{\textcolor{blue}{Proof: }}
\def\case#1{\textcolor{blue}{Case \uppercase\expandafter{\romannumeral#1}: }}

% \newmdtheoremenv{lemma}{Lemma}
% \newmdtheoremenv{theorem}{\textcolor{red}{Theorem}}
% \newmdtheoremenv{defi}{\textcolor{blue}{Definition}}
\newenvironment{md}{\begin{mdframed}}{\end{mdframed}}

\graphicspath{{figures/}}

% \begin{document}
% \title{<++>}
\author{Name}
% \maketitle
% \end{document}
```

## ln_preamble.tex

该文件用于配制定理、页脚页眉等环境，通常用于 Leture Notes 的文件中。

```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhead[L]{\slshape{Haoyu Zhen}}

% theorems
\usepackage{thmtools}
\usepackage{thm-restate}
\usepackage[framemethod=TikZ]{mdframed}
\mdfsetup{skipabove=1em,skipbelow=0em, innertopmargin=12pt, innerbottommargin=8pt}

\theoremstyle{definition}

\declaretheoremstyle[headfont=\bfseries\sffamily, bodyfont=\normalfont,
	mdframed={
		nobreak,
		backgroundcolor=brown!14,
		topline=false,
		rightline=false,
		leftline=true,
		bottomline=false,
		linewidth=2pt,
		linecolor=brown!180,
	}
]{thmbrownbox}

\declaretheoremstyle[headfont=\bfseries\sffamily, bodyfont=\normalfont,
	mdframed={
		nobreak,
		backgroundcolor=Blue!4,
		topline=false,
		rightline=false,
		leftline=true,
		bottomline=false,
		linewidth=2pt,
		linecolor=NavyBlue!120,
	}
]{thmbluebox}

\declaretheoremstyle[headfont=\bfseries\sffamily, bodyfont=\normalfont,
	mdframed={
		nobreak,
		backgroundcolor=Green!5,
		topline=false,
		rightline=false,
		leftline=true,
		bottomline=false,
		linewidth=2pt,
		linecolor=OliveGreen!120,
	}
]{thmgreenbox}

\declaretheoremstyle[headfont=\bfseries\sffamily, bodyfont=\normalfont,
	mdframed={
		nobreak,
		topline=false,
		rightline=false,
		leftline=true,
		bottomline=false,
		linewidth=2pt,
		linecolor=OliveGreen!120,
	}
]{thmgreenline}

\declaretheoremstyle[headfont=\bfseries\sffamily, bodyfont=\normalfont,
	mdframed={
		nobreak,
		topline=false,
		rightline=false,
		leftline=true,
		bottomline=false,
		linewidth=2pt,
		linecolor=NavyBlue!70,
	}
]{thmblueline}

\declaretheorem[numberwithin=section, style=thmbrownbox, name={\color{Brown}Definition}]{defi}
\declaretheorem[numberwithin=section, style=thmgreenbox, name={\color{OliveGreen}Law}]{law}
\declaretheorem[numberwithin=section, style=thmbluebox, name={\color{Blue}Corollary}]{cor}
\declaretheorem[numberwithin=section, style=thmgreenline, name={\color{OliveGreen}Property}]{prt}
\declaretheorem[numberwithin=section, style=thmbluebox, name={\color{Blue}Proposition}]{prp}
\declaretheorem[numberwithin=section, style=thmbluebox, name={\color{Blue}Theorem}]{thm}
\declaretheorem[numberwithin=section, style=thmbluebox, name={\color{Blue}Lemma}]{lemma}
\declaretheorem[numberwithin=section, style=thmbrownbox,  name={\color{NavyBrown}Example}]{eg}
\declaretheorem[numberwithin=section, style=thmgreenline, name={\color{OliveGreen}Remark}]{remark}
\declaretheorem[numbered=no,style=thmblueline, name={\color{NavyBlue!70}Proof},qed=$\square$]{prf}
```

{% include links.html %}