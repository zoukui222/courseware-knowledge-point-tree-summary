# Changelog

本文件记录 `courseware-knowledge-point-tree-summary` skill 的版本变更，与 `VERSION` 及 `SKILL.md` frontmatter 的 `version` 三者保持一致。

## [1.1.0] - 2026-11-03

- 从 `knowledge-tree-summary` 更名为 `courseware-knowledge-point-tree-summary`（「课件_知识点树形总结」的英文翻译）。
- 新增规则：**PDF 课件先转 PPT（pptx）再调取**——用 `soffice --headless --convert-to pptx` 或 Office / WPS 另存，转完再走 pptx 读取流程，保证每页标题与表格抽取最稳；环境无转换工具时退化为读 PDF 文本层，并主动告知用户表格精确度会降。
- 保留 v1.0.0 全部规则：叶子精确到表格每一项、两版 md 交付、程序化统计、不夹带源文件没有的内容、ASCII 树 `├─`/`└─` 对齐校准。

## [1.0.0] - 2026-11-03

- 初始版本：建立「课件 → 知识树」流程（读取 → 建树 → 两版 md → 程序化统计），并沉淀陷阱（不许伪造知识点、统计数字必须实算、删节点后校准 `└─`）。
