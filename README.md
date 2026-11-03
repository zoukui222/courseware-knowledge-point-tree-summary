# courseware-knowledge-point-tree-summary

给 Hermes Agent 用的一个 skill：把 PPT / PDF 课件总结成**树形知识树**，叶子精确到知识点表格的每一项（每行拆成一句自然语言）。

## 是什么

一份 `SKILL.md`，编码了「课件 → 知识树」的完整流程：

- 读取 `.pptx`（PDF 先转 PPT）抽取文本骨架。
- 按「章节 → 小节 → 知识点 → 表格行（叶子）」建树，表格每一项都拆成独立叶子。
- 产出两版 Markdown：**文字版**（标题 + 表格还原）+ **结构树版**（整棵 ASCII 树，`├─` / `└─` / `│` 对齐）。
- 末尾附**程序化统计**（一级分支数、节点数、叶子数、表格张数与行数），全部脚本实算，不写约数。

## 怎么安装

这是 Hermes Agent 的 user skill。把本目录整个放到 Hermes 的 skills 目录下：

```
%LOCALAPPDATA%\hermes\skills\<category>\courseware-knowledge-point-tree-summary\
```

（Windows；`<category>` 可用 `productivity`，或你的自定义分类。）放好后 Hermes 会自动扫描到它，下次会话即可通过描述命中。

SKILL.md 的 frontmatter 已经写好 `name` / `description` / `version`，无需再改。

## 怎么用 / 产出什么

在 Hermes 里对课件说一句「总结这个课件」或「画知识树」，它会加载这个 skill 并：

1. 读源文件（`.pptx` 直接读；`.pdf` 先 `soffice --convert-to pptx` 或用 Office/WPS 另存）。
2. 生成两个 `.md`，默认跟源文件放同一目录：
   - `*_知识树_文字版.md` —— 阅读、背记。
   - `*_知识树_结构树.md` —— 一眼看全局的 ASCII 树。
3. 文件末尾带实算统计。

## 不做什么

- 不生成教程 HTML（那是 `runoob-style-tutorial` 的活）。
- 不改简历、不改项目描述。
- 不夹带源文件里没有的知识点——用户要「最精确」时，编造一句就算伪造，交付前逐条比对源文件删掉。

## 版本

见 `VERSION`（当前 1.1.0）与 `CHANGELOG.md`。
