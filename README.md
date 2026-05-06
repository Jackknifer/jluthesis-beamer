# 吉林大学数学学院毕业论文答辩 Beamer 模板

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![LaTeX](https://img.shields.io/badge/Language-LaTeX-blue.svg)](https://www.latex-project.org/)
[![XeLaTeX](https://img.shields.io/badge/Compiler-XeLaTeX-informational.svg)](https://tug.org/xetex/)

## 📖 项目简介

本项目提供了一套**开箱即用**的吉林大学数学学院毕业论文答辩 Beamer 演示模板。

模板采用吉林大学数学学院视觉标识配色，内置封面页、目录页、章节过渡页、正文页、参考文献页和结束页，使用者只需替换论文信息和正文内容即可生成规范、美观的答辩 PPT。

**模板特性**：
- 🎨 吉大蓝主题色，封面 / 结束页 / 页眉页脚统一视觉风格
- 📐 自适应封面布局：标题行数变化时，答辩信息块自动跟随
- 🔢 页眉章节导航，页脚显示答辩人 / 日期 / 页码
- 📦 内置 block、exampleblock、alertblock 三种块环境（tcolorbox 美化）
- 📑 参考文献使用 BibTeX + GB/T 7714 国标格式管理
- 🖋️ 本地中文字体，XeLaTeX 编译，跨平台可用

---

## 📂 项目结构说明

请务必保持以下目录结构，**不要随意删除或移动文件夹**，否则编译会报错。

```text
jlu-thesis-defense-beamer-template/
├── assets/                                # [资源] 模板 Logo 图片
│   ├── jlu_math_logo_navy.png             #   深色 Logo（封面/结束页）
│   └── jlu_math_logo_white.png            #   白色 Logo（页眉）
├── fonts/                                 # [核心] 中文字体文件
│   ├── SimHei.TTF                         #   黑体（标题强调）
│   ├── SimKai.TTF                         #   楷体（正文主字体）
│   └── SimSun.TTC                         #   宋体（等宽备用）
├── images/                                # [资源] 用户插图文件夹
│   └── .gitkeep                           #   占位，保证空目录被 Git 跟踪
├── .gitignore                             # Git 忽略规则
├── .latexmkrc                             # latexmk 编译配置
├── LICENSE                                # MIT 开源许可证
├── README.md                              # 本说明文件
├── references.bib                         # [数据] 参考文献数据库
├── jlu_math_thesis_defense_beamer.tex     # [入口] 模板主文件
└── jlu_math_thesis_defense_beamer.pdf     # 当前预览 PDF
```

> **说明**：编译产生的辅助文件（`.aux`、`.log`、`.nav`、`.out`、`.snm`、`.toc`、`.vrb`、`.synctex.gz`、`.bbl`、`.blg` 等）已在 `.gitignore` 中排除，不会提交到仓库。

---

## 🛠️ 环境准备

你可以选择**本地安装**（推荐长期使用）或**在线编辑**（Overleaf，推荐不想安装软件的同学）。

### 方案一：在线编辑 (Overleaf)

1. **打包项目**：将本模板的所有文件（包括 `fonts/`、`assets/`、`images/` 等）打成 `.zip` 压缩包。
2. **上传**：登录 [Overleaf](https://www.overleaf.com/)，点击 "New Project" → "Upload Project"，上传压缩包。
3. **设置编译器（关键）**：
   - 点击左上角菜单 (Menu)。
   - 将 "Compiler" 设置为 **XeLaTeX**（否则中文会乱码）。
   - 点击 "Recompile" 即可预览。

### 方案二：本地安装 (TeX Live + 编辑器)

#### 1. 安装 TeX 发行版

推荐安装 **TeX Live** (Windows/Linux) 或 **MacTeX** (macOS)。

- **下载地址**：[吉林大学开源镜像站](https://mirrors.jlu.edu.cn/CTAN/systems/texlive/Images/)（下载 `texlive.iso`）
- macOS 用户也可通过 Homebrew：`brew install --cask mactex`

#### 2. 安装编辑器

**选项 A：Visual Studio Code（推荐）**

- 安装插件 [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)。
- **配置教程**：参考 [VS Code 配置 LaTeX - 知乎](https://zhuanlan.zhihu.com/p/166523064)。
- 编译方式：使用侧边栏 TeX 面板中的 `latexmk (xelatex)` recipe。

**选项 B：TeXstudio（适合新手）**

- **下载地址**：[TeXstudio 官网](https://www.texstudio.org/)
- 打开后：`Options` → `Configure TeXstudio` → `Build` → 将默认编译器改为 **XeLaTeX**。

---

## 🔨 编译方法

本模板使用 **XeLaTeX** 编译。完整编译链如下：

```bash
xelatex jlu_math_thesis_defense_beamer.tex
bibtex  jlu_math_thesis_defense_beamer
xelatex jlu_math_thesis_defense_beamer.tex
xelatex jlu_math_thesis_defense_beamer.tex
```

> ⚠️ **不要只运行一次 xelatex**。Beamer 的目录、页眉导航、PDF 书签和总页数需要至少两轮编译才能稳定。加入参考文献后还需要 bibtex 那一步。

如果安装了 `latexmk`，也可以一键编译（项目已配置 `.latexmkrc`）：

```bash
latexmk jlu_math_thesis_defense_beamer.tex
```

清除辅助文件：

```bash
latexmk -c
```

---

## 📝 常用功能

### 插入图片

将图片文件放入 `images/` 文件夹，然后在 frame 中引用：

```latex
\begin{frame}{实验结果}
  \begin{figure}
    \centering
    \includegraphics[width=0.8\textwidth]{images/result_curve.pdf}
    \caption{实验结果曲线}
  \end{figure}
\end{frame}
```

图片格式建议优先使用 PDF（矢量图质量最佳），也支持 PNG、JPG。

### 图文并排

使用 `columns` 环境实现左右分栏：

```latex
\begin{columns}[T,totalwidth=\textwidth]
  \begin{column}{.48\textwidth}
    \includegraphics[width=\textwidth]{images/your_figure.pdf}
  \end{column}
  \begin{column}{.48\textwidth}
    \begin{itemize}
      \item 说明一
      \item 说明二
    \end{itemize}
  \end{column}
\end{columns}
```

### 表格

推荐使用 `booktabs` 三线表：

```latex
\begin{table}
  \centering
  \caption{实验对比结果}
  \begin{tabular}{lcc}
    \toprule
    方法 & 指标 A & 指标 B \\
    \midrule
    基线方法 & 0.812 & 0.764 \\
    本文方法 & \alert{0.879} & \alert{0.823} \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 数学公式

```latex
\begin{equation*}
  F(x) = \int_{a}^{b} f(t,x)\,\mathrm{d}t, \qquad \nabla F(x) = 0.
\end{equation*}
```

答辩中建议只放最核心的公式，并在公式下方用列表解释符号含义。

### 代码展示

```latex
\begin{frame}[fragile]{算法实现}
\begin{lstlisting}[language=Python]
def model_step(x, theta):
    score = objective(x, theta)
    return score
\end{lstlisting}
\end{frame}
```

> 包含 `lstlisting` 的 frame 必须加 `[fragile]` 选项。

### 块环境

模板提供三种美化过的 block 环境：

```latex
\begin{block}{普通 block}          % 蓝灰色，用于定义/说明
  内容...
\end{block}

\begin{exampleblock}{示例 block}    % 浅蓝色，用于示例/实验
  内容...
\end{exampleblock}

\begin{alertblock}{警示 block}      % 淡红色，用于关键结论
  内容...
\end{alertblock}
```

### 参考文献

参考文献统一写在 `references.bib` 中，正文使用 `\cite{key}` 引用：

```latex
根据张三等人的研究~\cite{example_article}，...
```

模板末尾已配置参考文献页面：

```latex
\begin{frame}[t]{参考文献}
  \scriptsize
  \bibliographystyle{gbt7714-numerical}
  \nocite{*}
  \bibliography{references}
\end{frame}
```

- `\nocite{*}` 会列出 `.bib` 中所有文献，如果只想显示正文引用的，删去此行。
- 编译后如果引用显示为 `[?]`，请完整执行 `xelatex → bibtex → xelatex × 2` 编译链。

### 强调文字

```latex
\JLUEmph{黑体强调}     % 切换为黑体
\alert{蓝色高亮}        % Beamer alert 样式
```

---

## ❓ 常见问题

**Q1：编译后中文全是乱码或方框？**

A：确保使用 **XeLaTeX** 编译器（不是 pdfLaTeX）。同时确认 `fonts/` 文件夹完整存在。

**Q2：参考文献显示为 `[?]`？**

A：需要完整编译链 `xelatex → bibtex → xelatex × 2`。使用 `latexmk` 会自动处理。

**Q3：编译报错 `File 'references.bib' not found`？**

A：确认 `references.bib` 文件在项目根目录。如果暂时不需要参考文献，注释掉 `\bibliography{references}` 那一行。

**Q4：如何增减章节数量？**

A：修改章节标题命令后，还需要同步修改两处：
1. `\JLUOutline` 中的 `\JLUOutlineEntry`（目录页）
2. `\JLUSectionNavigation` 中的 `\JLUSectionNavigationEntry`（页眉导航）

**Q5：Overleaf 上编译超时？**

A：检查图片文件大小（建议单张不超过 2MB），或者删减字体文件（只保留实际使用的字体）。

**Q6：封面标题换成一行后下面空了很大一块？**

A：这是正常的自适应行为。如果视觉上需要收紧，可以微调 `\JLUCoverTitleTopY` 使标题下移。

---

## 🤝 贡献与反馈

如果你在使用过程中遇到编译失败、版式偏差或说明不清晰等问题，欢迎通过 [GitHub Issues](https://github.com/Jackknifer/jlu-thesis-defense-beamer-template/issues) 反馈。

---

## ⚠️ 声明

本模板是一个吉林大学数学学院毕业论文答辩 Beamer 演示模板，旨在帮助同学们快速制作规范、美观的答辩演示文稿。

**❗️ 重要提示：**

1. **非官方版本**：吉林大学及数学学院官方并未发布、授权或认证过任何答辩 Beamer 模板。
2. **仅供参考**：本模板是作者根据学院视觉标识和常见答辩结构制作的，不保证完全符合所有老师的要求。
3. **使用须知**：请根据自身情况及导师要求自行决定是否使用。

---

## 📜 许可证

本项目采用 [MIT 许可证](LICENSE) 开源。
