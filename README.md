# 吉林大学数学学院 Beamer 模板

这是基于 Beamer/XeLaTeX 的吉林大学数学学院答辩演示模板。

## 文件

- `reference_reconstruction.tex`: 最终模板源文件
- `reference_reconstruction.pdf`: 当前预览 PDF
- `assets/`: 模板中使用的图片资源
- `fonts/`: 模板中使用的中文字体

## 编译

```bash
latexmk -xelatex -interaction=nonstopmode -halt-on-error reference_reconstruction.tex
```

模板使用本地字体和图片资源，编译时请保留 `assets/` 与 `fonts/` 目录。
