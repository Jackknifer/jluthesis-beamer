# 吉林大学 Beamer 答辩模板库

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![LaTeX](https://img.shields.io/badge/Language-LaTeX-blue.svg)](https://www.latex-project.org/)
[![XeLaTeX](https://img.shields.io/badge/Compiler-XeLaTeX-informational.svg)](https://tug.org/xetex/)

本仓库用于维护两个相互独立、可单独打包使用的吉林大学毕业论文答辩 Beamer 模板：

- `jlu/`：吉林大学校级通用模板。
- `math/`：吉林大学数学学院模板。

两个模板都内置封面页、目录页、章节过渡页、正文页、参考文献页和结束页。使用者通常只需要替换论文信息、章节标题、正文内容、图片和参考文献。

## 项目结构

```text
jlu-thesis-defense-beamer-template/
├── jlu/                         # 校级模板
│   ├── assets/                  # 校徽、校名、校训及派生 PNG 资源
│   ├── fonts/                   # 模板内置中文字体
│   ├── images/                  # 用户图片目录
│   ├── jlu_defense.tex          # 校级模板入口
│   ├── jlu_defense.pdf          # 校级模板预览
│   ├── jlu_cover_test.tex       # 传统封面对比测试文件
│   ├── references.bib           # 参考文献数据库
│   └── .latexmkrc               # 编译配置
├── math/                        # 数学学院模板
│   ├── assets/                  # 数学学院院徽及派生 PNG 资源
│   ├── fonts/                   # 模板内置中文字体
│   ├── images/                  # 用户图片目录
│   ├── math_defense.tex         # 数学学院模板入口
│   ├── math_defense.pdf         # 数学学院模板预览
│   ├── references.bib           # 参考文献数据库
│   └── .latexmkrc               # 编译配置
├── .gitignore
├── LICENSE
└── README.md
```

每个模板目录都是完整项目，字体、素材、参考文献和编译配置互不依赖。建议从对应模板目录内编译，不要在仓库根目录直接编译子目录里的 `.tex`。

## 快速开始

本地编译需要安装 TeX Live 或 MacTeX，并使用 XeLaTeX。

编译校级模板：

```bash
cd jlu
latexmk jlu_defense.tex
```

编译校级传统封面对比页：

```bash
cd jlu
latexmk jlu_cover_test.tex
```

编译数学学院模板：

```bash
cd math
latexmk math_defense.tex
```

手动编译链为：

```bash
xelatex <main>.tex
bibtex <main>
xelatex <main>.tex
xelatex <main>.tex
```

其中 `<main>` 分别为 `jlu_defense` 或 `math_defense`。

## Overleaf 使用

如果只需要一个模板，建议只打包对应目录：

- 校级模板：打包 `jlu/` 目录。
- 数学学院模板：打包 `math/` 目录。

上传到 Overleaf 后，将编译器设置为 XeLaTeX，再编译主文件。

## 常用修改位置

在主 `.tex` 文件开头的论文信息区修改：

- `\ThesisTitle`：论文题目。
- `\ThesisSubtitle`：答辩类型，默认“毕业论文答辩”。
- `\AuthorName`、`\StudentID`、`\SupervisorName`：答辩人信息。
- `\DepartmentName`、`\DepartmentShortName`：学校或学院显示文本。
- `\MajorName`、`\DefenseDate`：专业和答辩日期。

新增正文页时，复制：

```latex
\begin{frame}{页面标题}
  页面内容
\end{frame}
```

新增章节时，添加 `\section{章节名}`。如果希望目录页和页眉导航完全同步，也要同步维护文件中定义的章节标题命令和目录条目。

## 资源说明

`assets/` 中保留了原始高清图片，也包含模板直接引用的透明 PNG：

- 数学学院模板保留 `jlu_math_logo_source.png`，实际使用 `jlu_math_logo_navy.png` 和 `jlu_math_logo_white.png`。
- 校级模板保留 `jd-xhh-2.jpg`、`jd-xm.jpg`、`jd-xx.jpg`，实际使用 `jlu_logo_navy.png`、`jlu_logo_white.png`、`jlu_name_blue.png`、`jlu_name_white.png` 和 `jlu_motto_navy.png`。

`images/` 留给使用者放自己的图表、实验结果和插图。

## 常见问题

**中文乱码或方框**

请确认使用 XeLaTeX 编译，并保留对应模板目录下的 `fonts/` 文件夹。

**参考文献显示为 `[?]`**

需要完整编译链 `xelatex -> bibtex -> xelatex -> xelatex`。使用 `latexmk` 会自动处理。

**找不到 `references.bib`**

请从模板目录内编译。例如编译校级模板时先 `cd jlu`，编译数学学院模板时先 `cd math`。

**图片路径报错**

用户图片建议放入当前模板目录的 `images/` 文件夹，并用 `images/your-image.png` 这样的相对路径引用。

## 声明

本项目为非官方模板，未经过吉林大学或相关学院官方发布、授权或认证。模板仅供学习和答辩排版参考，正式使用前请根据导师、学院和学校要求自行确认。

## 许可证

本项目采用 [MIT 许可证](LICENSE) 开源。
