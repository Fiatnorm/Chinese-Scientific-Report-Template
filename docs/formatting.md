# 排版约定与排错

| 项目 | 模板默认 |
| --- | --- |
| 页面 | A4、单栏，正文四边距 25 mm；无页眉，页码从首页起以阿拉伯数字居中连续编号 |
| 题名 | 三号黑体居中；下一行排作者，再下一行排单位与日期 |
| 正文 | 小四 Fandol 宋体；西文 TeX Gyre Termes（Times 风格，不是 Times New Roman） |
| 段落 | 首行缩进两个汉字宽，段间不另加空距；行距采用 `\linespread{1.18}` 乘以基础基线距 |
| 标题 | 一级四号黑体，二级小四黑体，使用 `1`、`1.1` 编号；摘要、关键词和参考文献不编号 |
| 公式 | `equation` 适合单行，`align` 适合多行；可用 `\notag` 省略该行编号，保留的编号全文连续 |
| 图表 | 图题在下、表题在上，均为五号；三线表用 `booktabs`，小数对齐用 `siunitx` 的 `S` 列 |
| 参考文献 | Biber + `gb7714-2015` 顺序编码；兼顾较旧的 TeX Live，并不声称符合 GB/T 7714—2025 |

## 替换素材

- 曲线和示意图优先保存为 PDF 矢量图，照片可用 PNG/JPG。将文件放进 `figures/`，修改 `\includegraphics{figures/文件名}`。示例图由解析式 `y = 1 - exp(-θ)` 绘制，非实验数据。
- 文内先提及公式或图表，再排对应环境。`[htbp]` 是浮动位置建议，不保证原地出现；不要靠空行或强制分页推移图表。较长表格若需跨页，应重新选择表格环境并检查续表版式。
- 使用 `\qty{2}{\second}` 排量值，用 `\unit{\second}` 排单位。图中坐标轴、表头和正文宜统一符号和单位。
- 中文文献按实际类型新建条目（如 `@article`），填入 `author`、`title`、`journaltitle`、`date`、卷期及页码，中文条目可标记 `langid = {chinese}`；多位作者用 `and` 分隔。

## 常见问题

| 现象 | 排查 |
| --- | --- |
| 提示 pdfTeX、中文字体或引擎错误 | 使用 XeLaTeX；本地确认 TeX Live 中安装了 CTeX、Fandol、TeX Gyre。不要用本机系统字体掩盖依赖问题。 |
| `File ... not found` | 从仓库根目录编译 `main.tex`；检查图片和章节路径、扩展名、大小写。 |
| 编号为 `??` 或文献未生成 | 核对标签和文献键；让 latexmk 跑完整轮次。Overleaf 可选择 **Recompile from scratch**。本地确认 Biber 与 BibLaTeX 来自同一发行版。 |
| 个别罕见汉字不显示 | 查日志中的 `Missing character`；按实际字符范围另选有授权、可复现的字体，不直接提交商业字体。 |

## 参考依据

- [GB/T 7713.2—2022《学术论文编写规则》](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=0B963916637B8F34B295FCF4A51A1BE5)：用于参考论文组成和编排惯例；本模板的版心、字号、行距不是声称由该国标统一规定。
- [《电机与控制学报》论文模板](https://cddj.cbpt.cnki.net/EditorE2N/PromptPageInfo.aspx?c=3&t=v)：参考公式居中编号、图表题与三线表惯例，不直接沿用该刊的字号与投稿要求。
- [Overleaf 中文排版指南](https://www.overleaf.com/learn/latex/Chinese)及[复制项目说明](https://docs.overleaf.com/managing-projects-and-files/copying-a-project)：用于确认 CTeX、XeLaTeX 与复制流程。
