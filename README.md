# 吉林大学 Beamer 答辩模板库

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![LaTeX](https://img.shields.io/badge/Language-LaTeX-blue.svg)](https://www.latex-project.org/)
[![XeLaTeX](https://img.shields.io/badge/Compiler-XeLaTeX-informational.svg)](https://tug.org/xetex/)

本仓库维护三个可独立打包、独立编译的吉林大学毕业论文答辩 Beamer 模板：

- `jlu/`：吉林大学校级模板。
- `math/`：吉林大学数学学院模板。
- `jlu_v2/`：吉林大学模板 2，使用传统居中封面和统一尾页。

每个模板目录都包含完整的字体、素材、图片目录、参考文献文件、编译配置、主 `.tex` 文件和预览 PDF。使用者通常只需要替换论文信息、章节标题、正文内容、图片和参考文献。

## 项目结构

```text
jlu-thesis-defense-beamer-template/
├── jlu/                         # 吉林大学校级模板
│   ├── assets/                  # 校徽、校名、校训及派生 PNG 资源
│   ├── fonts/                   # 模板内置中文字体
│   ├── images/                  # 用户图片目录
│   ├── jlu_defense.tex          # 模板入口
│   ├── jlu_defense.pdf          # 预览 PDF
│   ├── references.bib           # 参考文献数据库
│   └── .latexmkrc               # 编译配置
├── math/                        # 吉林大学数学学院模板
│   ├── assets/                  # 数学学院院徽及派生 PNG 资源
│   ├── fonts/                   # 模板内置中文字体
│   ├── images/                  # 用户图片目录
│   ├── math_defense.tex         # 模板入口
│   ├── math_defense.pdf         # 预览 PDF
│   ├── references.bib           # 参考文献数据库
│   └── .latexmkrc               # 编译配置
├── jlu_v2/                      # 吉林大学模板 2
│   ├── assets/                  # 校级模板资源
│   ├── fonts/                   # 模板内置中文字体
│   ├── images/                  # 用户图片目录
│   ├── jlu_v2_defense.tex       # 模板入口
│   ├── jlu_v2_defense.pdf       # 预览 PDF
│   ├── references.bib           # 参考文献数据库
│   └── .latexmkrc               # 编译配置
├── .gitignore
├── LICENSE
└── README.md
```

建议从对应模板目录内编译，不要在仓库根目录直接编译子目录里的 `.tex`。

## 快速开始

本地编译需要安装 TeX Live 或 MacTeX，并使用 XeLaTeX。

编译吉林大学校级模板：

```bash
cd jlu
latexmk jlu_defense.tex
```

编译数学学院模板：

```bash
cd math
latexmk math_defense.tex
```

编译吉林大学模板 2：

```bash
cd jlu_v2
latexmk jlu_v2_defense.tex
```

手动编译链为：

```bash
xelatex <main>.tex
bibtex <main>
xelatex <main>.tex
xelatex <main>.tex
```

其中 `<main>` 分别为 `jlu_defense`、`math_defense` 或 `jlu_v2_defense`。

## Overleaf 使用

如果只需要一个模板，建议只打包对应目录：

- 校级模板：打包 `jlu/`。
- 数学学院模板：打包 `math/`。
- 校级模板 2：打包 `jlu_v2/`。

上传到 Overleaf 后，将编译器设置为 XeLaTeX，再编译对应主文件。

## 常用修改位置

在主 `.tex` 文件开头的论文信息区修改：

- `\ThesisTitle`：论文题目。
- `\ThesisSubtitle`：答辩类型，默认“毕业论文答辩”。
- `\AuthorName`、`\SupervisorName`：答辩人信息。
- `\DepartmentName`、`\DepartmentShortName`：学校或学院显示文本。
- `\CollegeName`：校级模板和模板 2 封面中的学院名称。
- `\MajorName`、`\DefenseDate`：专业和答辩日期。

新增正文页时，复制：

```latex
\begin{frame}{页面标题}
  页面内容
\end{frame}
```

新增章节时，添加 `\section{章节名}`。如果希望目录页和页眉导航完全同步，也要同步维护文件中定义的章节标题命令和目录条目。

## 资源命名

`assets/` 中保留原始高清图片和模板直接引用的透明 PNG：

- 校级模板和模板 2 使用 `jlu_logo_source.jpg`、`jlu_name_source.jpg`、`jlu_motto_source.jpg` 作为原始素材。
- 校级模板和模板 2 实际引用 `jlu_logo_navy.png`、`jlu_logo_white.png`、`jlu_name_blue.png`、`jlu_name_white.png` 和 `jlu_motto_navy.png`。
- 数学学院模板保留 `jlu_math_logo_source.png`，实际引用 `jlu_math_logo_navy.png` 和 `jlu_math_logo_white.png`。

`images/` 留给使用者放自己的图表、实验结果和插图。

## 发布包

发布时每个模板单独打包为 zip：

- `jlu-template.zip`
- `math-template.zip`
- `jlu-v2-template.zip`

每个 zip 都只包含对应模板目录，不包含仓库中的临时文件或其他模板。

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
