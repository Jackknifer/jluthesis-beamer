# 吉林大学数学学院 Beamer 模板

这是基于 Beamer/XeLaTeX 的吉林大学数学学院答辩演示模板。

## 文件

- `jlu_math_thesis_defense_beamer.tex`: 最终模板源文件
- `jlu_math_thesis_defense_beamer.pdf`: 当前预览 PDF
- `assets/`: 模板中使用的图片资源
- `fonts/`: 模板中使用的中文字体
- `references/`: 可选的本地参考模板目录，默认不纳入 Git

## 编译

```bash
latexmk -xelatex -interaction=nonstopmode -halt-on-error jlu_math_thesis_defense_beamer.tex
```

模板使用本地字体和图片资源，编译时请保留 `assets/` 与 `fonts/` 目录。
若需要继续参考其他学校模板，建议放入 `references/`，避免污染最终模板仓库。
