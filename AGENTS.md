# AGENTS.md

## 范围与入口

- 这是可复制的中文科技短报告模板，不是期刊投稿、学位论文或特定实验项目。
- `main.tex` 是唯一编译入口；排版写在 `preamble.tex`，示例正文放在 `sections/`，图件在 `figures/`，文献在 `references.bib`。
- LaTeX、BibLaTeX 与 Markdown 使用 UTF-8；路径相对于根目录，大小写须与磁盘文件一致。

## 编辑约定

- 保持 XeLaTeX + Biber 可用，并保留 Fandol 与 TeX Gyre Termes 作为可移植默认字体；不依赖系统商业字体、shell escape 或未提交图片。
- 正文用空行分段；不要用空格、`\\` 或空段手工制造段落缩进和分页。
- 保留可复用的公式、外部图片、三线表和文献示例。标签紧跟图表的 `\caption`，维持 `eq:`、`fig:`、`tab:` 前缀。
- 更改入口、目录或排版约定时同步更新 `README.md` 与 `docs/formatting.md`；不提交报告编译产物、真实个人数据或未授权图片。

## 验证

- 在根目录运行 `latexmk -xelatex -interaction=nonstopmode -halt-on-error -file-line-error -outdir=build main.tex`，确保无缺字、未定义引用或溢出版心。
- 排版变更后逐页检查 `build/main.pdf`：标题、二字缩进、页脚连续页码、公式编号、先引用后出图表、图表题位置、参考文献。
- `.github/workflows/latex.yml` 在干净环境编译样稿。变更依赖时同时验证 CI，不额外要求本机绘图环境。
