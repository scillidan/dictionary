
https://github.com/simon-pfahler/colorblind

```md
**Colorblind**, a LaTeX package, provides essential tools for colorblind-safe typesetting. This project addresses accessibility in documents by offering color schemes that maintain clarity for people with color vision deficiencies. By redefining standard colors, it ensures that text and graphics are easily distinguishable, promoting inclusivity in academic and professional presentations. The package is ideal for researchers, students, and anyone seeking to create documents that are accessible to all audiences.

Tags: `LaTeX`, `accessibility`, `typesetting`, `colorblind`, `packages`
```

```md
**Colorblind** 是一个 LaTeX 宏包，提供了色盲安全排版的基本工具。该项目通过提供适合色觉障碍者的配色方案，解决了文档的无障碍问题。通过重新定义标准颜色，它确保文本和图形易于区分，促进学术和专业演示的包容性。该宏包非常适合研究人员、学生以及任何希望创建面向所有受众的无障碍文档的人士使用。

标签：`LaTeX`，`无障碍`，`排版`，`色盲`，`宏包`
```

https://github.com/simon-pfahler/colorblind/blob/main/colorblind_doc.tex

````md
This LaTeX document defines a complete article using the `scrartcl` document class, which is part of the KOMA-Script bundle often used in German documents. The document focuses on presenting safe color schemes for accommodating people with color vision deficiencies, specifically using the `colorblind` package developed by Simon Pfahler. Let’s break down the major components of the document step-by-step.

### 1. Document Metadata

```tex
\DocumentMetadata{lang = en-us}
```

This line sets the metadata for the document, specifying that the language is English (U.S.).

### 2. Document Class

```tex
\documentclass{scrartcl}
```

This specifies that the document is of type `scrartcl`, a class for articles in the KOMA-Script family.

### 3. Package Inclusion

#### Geometry

```tex
\usepackage[left=4.5cm,right=3cm,top=3cm,bottom=3cm, marginpar=4cm]{geometry}
```

This package adjusts the margins of the document. The parameter specifies the left, right, top, bottom margins, and the width of the margin notes.

#### Color, Highlight, and TikZ

```tex
\usepackage{xcolor}
\usepackage{soul}
\usepackage{tikz}
\usetikzlibrary{positioning, shapes, fit, arrows.meta, decorations.pathmorphing, math}
```

- `xcolor`: Used for color handling.
- `soul`: Provides support for highlighting text.
- `tikz`: Used for creating graphics programmatically.

#### PGFPlots

```tex
\usepackage{pgfplots, pgfplotstable}
\pgfplotsset{compat=1.18}
```

Includes the `pgfplots` and `pgfplotstable` packages to create plots and tables effectively.

#### Hyperref and Cleveref

```tex
\usepackage{hyperref}
\hypersetup{
    pdftitle={Easy colorblind-safe typesetting: the colorblind package},
    pdfauthor={Simon Pfahler},
}
\usepackage{cleveref}
```

- `hyperref`: Enhances links within the document and in the generated PDF.
- `cleveref`: Automatically formats references to figures, sections, etc.

#### Bibliography

```tex
\usepackage[backend=biber, style=numeric-comp, seconds=true, sorting=none, subentry=true, doi=false, alldates=iso]{biblatex}
\addbibresource{bib.bib}
```

This includes the `biblatex` package to manage bibliographies with the `biber` backend, and it specifies the style and options for citations. The bibliography data will be pulled from a file named `bib.bib`.

#### Colorblind Package

```tex
\usepackage[keep-defaults, Tol, OkabeIto, pgf]{colorblind}
```

This tells LaTeX to use the `colorblind` package with specific options to provide color schemes for colorblind-safe typesetting.

### 4. Custom Commands

Here, several custom commands are defined for convenience. Examples include:

```tex
\newcommand\colorblind{\textbf{colorblind}}
\newcommand\hlc[2][T-Q-PH4]{{%
    \colorlet{foo}{#1}%
    \sethlcolor{foo}\hl{#2}}%
}
```

The `\colorblind` command formats the text "colorblind" in bold, and `\hlc` allows highlighting text in a specified (or default) color.

### 5. Document Structure

The body of the document starts with `\begin{document}` and includes sections, subsections, figures, and an abstract. 

The first part is an abstract describing the purpose of the `colorblind` package.

```tex
\begin{abstract}
    In colorblind-safe documents, the contents are presented in a way that the same information is...
\end{abstract}
```

The body includes multiple sections with explanations of color schemes, guided design rules, and examples of usage.

### 6. Figures and Color Schemes

Figures are created using `tikz` to illustrate various colors. For example:

```tex
\begin{figure}[ht]
    \centering
    \begin{tikzpicture}
        ...
    \end{tikzpicture}
    \caption{Redefinitions of the default \LaTeX\ colors.}
\end{figure}
```

This creates a figure centered in the document, illustrating color redefinitions.

### 7. Bibliography

The document ends with the printing of the bibliography:

```tex
\printbibliography
```

### Summary

This document is a complete LaTeX article that provides guidelines for creating documents that are safe for people with color vision deficiencies. It demonstrates how to set up a document with custom margins, utilize color carefully, and manage bibliographic references effectively.

For further details on the `colorblind` package, you can visit [CTAN - colorblind](https://ctan.org/pkg/colorblind).
````

````md
这份 LaTeX 文档使用 `scrartcl` 文档类定义了一个完整的文章，`scrartcl` 是 KOMA-Script 套件的一部分，通常用于德语文档。本文档重点介绍了为色觉障碍者设计的安全配色方案，特别是使用由 Simon Pfahler 开发的 `colorblind` 宏包。下面我们逐步解析该文档的主要组成部分。

### 1. 文档元数据

```tex
\DocumentMetadata{lang = en-us}
```

这行代码设置了文档的元数据，指定语言为英语（美国）。

### 2. 文档类

```tex
\documentclass{scrartcl}
```

指定文档类型为 `scrartcl`，这是 KOMA-Script 族中用于文章的文档类。

### 3. 宏包导入

#### Geometry

```tex
\usepackage[left=4.5cm,right=3cm,top=3cm,bottom=3cm, marginpar=4cm]{geometry}
```

该宏包用于调整文档的页边距，参数分别指定了左、右、上、下边距以及边注宽度。

#### 颜色、高亮和 TikZ

```tex
\usepackage{xcolor}
\usepackage{soul}
\usepackage{tikz}
\usetikzlibrary{positioning, shapes, fit, arrows.meta, decorations.pathmorphing, math}
```

- `xcolor`：处理颜色相关功能。
- `soul`：支持文本高亮。
- `tikz`：用于程序化绘制图形。

#### PGFPlots

```tex
\usepackage{pgfplots, pgfplotstable}
\pgfplotsset{compat=1.18}
```

引入 `pgfplots` 和 `pgfplotstable` 宏包，以便有效绘制图形和表格。

#### 超链接与智能引用

```tex
\usepackage{hyperref}
\hypersetup{
    pdftitle={Easy colorblind-safe typesetting: the colorblind package},
    pdfauthor={Simon Pfahler},
}
\usepackage{cleveref}
```

- `hyperref`：增强文档内及生成 PDF 中的链接功能。
- `cleveref`：自动格式化对图形、章节等的引用。

#### 参考文献管理

```tex
\usepackage[backend=biber, style=numeric-comp, seconds=true, sorting=none, subentry=true, doi=false, alldates=iso]{biblatex}
\addbibresource{bib.bib}
```

引入 `biblatex` 宏包，使用 `biber` 作为后端，指定引用样式及选项。参考文献数据来自 `bib.bib` 文件。

#### Colorblind 宏包

```tex
\usepackage[keep-defaults, Tol, OkabeIto, pgf]{colorblind}
```

该行启用 `colorblind` 宏包并设置选项，以提供适合色觉障碍者的配色方案。

### 4. 自定义命令

文档中定义了一些便捷的自定义命令。例如：

```tex
\newcommand\colorblind{\textbf{colorblind}}
\newcommand\hlc[2][T-Q-PH4]{{%
    \colorlet{foo}{#1}%
    \sethlcolor{foo}\hl{#2}}%
}
```

`\colorblind` 命令将“colorblind”这个词加粗显示，`\hlc` 命令用于以指定（或默认）颜色高亮文本。

### 5. 文档结构

正文部分以 `\begin{document}` 开始，包含章节、小节、图形及摘要。

开头是关于 `colorblind` 宏包用途的摘要：

```tex
\begin{abstract}
    In colorblind-safe documents, the contents are presented in a way that the same information is...
\end{abstract}
```

正文包括多个章节，介绍配色方案、设计指导原则及使用示例。

### 6. 图形与配色方案

文档通过 `tikz` 绘制图形以展示各种颜色。例如：

```tex
\begin{figure}[ht]
    \centering
    \begin{tikzpicture}
        ...
    \end{tikzpicture}
    \caption{Redefinitions of the default \LaTeX\ colors.}
\end{figure}
```

该图形居中显示，用于说明默认 LaTeX 颜色的重新定义。

### 7. 参考文献

文档以打印参考文献结尾：

```tex
\printbibliography
```

### 总结

这是一篇完整的 LaTeX 文章，提供了为色觉障碍人士设计安全文档的指导原则。文档示范了如何设置自定义页边距、谨慎运用颜色以及高效管理参考文献。

如需进一步了解 `colorblind` 宏包，可访问 [CTAN - colorblind](https://ctan.org/pkg/colorblind)。
````