# 中文科技小汇报 LaTeX 模板

面向组会、课程小论文和阶段技术汇报。采用 A4 单栏小论文版式，首页直接排题名、作者、单位、摘要和正文，无独立封面。示例以一阶系统阶跃响应为题，展示数学公式、矢量图片、三线表、交叉引用及参考文献。

## 在 Overleaf 使用

1. 在 GitHub 选择 **Code → Download ZIP**，将压缩包上传至 Overleaf：**New Project → Upload Project**。
2. 将 **Main document** 设为 `main.tex`，**Compiler** 选 **XeLaTeX**，然后点击 **Recompile**。文献由构建流程调用 Biber，不需要另行上传字体。
3. 保留一份不写正文的模板项目。每次写新报告，在 Overleaf 中 **Copy Project**；若需要独立 GitHub 仓库，可直接选 **Use this template**。复制品不会跟随模板自动更新。

## 在本地编译

安装 TeX Live（需包含 XeLaTeX、latexmk、Biber、CTeX/Fandol、TeX Gyre、`biblatex-gb7714-2015` 和 `siunitx` v3），在仓库根目录运行：

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error -file-line-error -outdir=build main.tex
```

输出 `build/main.pdf`。GitHub 仓库的 **Actions → Build LaTeX → 成功运行 → Artifacts** 也提供样稿 PDF（需要登录 GitHub，产物有保留期限）。

## 写作入口

| 路径 | 用途 |
| --- | --- |
| `main.tex` | 修改题名、作者、单位、日期、摘要、关键词和章节顺序 |
| `sections/` | 按引言、模型与方法、结果与讨论、结论编辑正文 |
| `figures/` | 放置图片；自带一张示例矢量曲线，不必生成后再编译 |
| `references.bib` | 维护文献条目；用 `\parencite{键}` 在正文引用 |
| `preamble.tex` | 集中维护字号、段落、页码、标题、图表题和引文样式 |

正文用空行分段；公式、图、表用 `eq:`、`fig:`、`tab:` 标签，并通过 `\eqref` 或 `\ref` 引用。图片路径以项目根目录为基准，文件名推荐使用小写英文、数字和连字符。详见[排版约定与排错](docs/formatting.md)。

模板参考中文学术论文的一般结构和图表惯例，不是指定期刊投稿或学位论文模板。若有学校、课程或期刊的具体要求，以对方格式为准。
