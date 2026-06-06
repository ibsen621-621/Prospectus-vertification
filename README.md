# 港股招股章程数据复核 Gem（HK Prospectus Validation Gem）

一套用于**港股 IPO 招股章程**数据复核的 Google Gemini Gem，针对前后不一致、勾稽不成立、
错别字、**中英文双语不对应**、HKEX 披露遗漏等问题做系统化排查，降低低级错误概率。

> 免责声明：本工具为复核辅助，不构成法律 / 会计 / 监管意见。所有疑点须经持牌专业人士
> 复核确认后据以修改；以 HKEX/SFC 现行规则原文为准。

## 仓库结构
- `gem-instructions.md` —— 粘贴到 Gem「指令（Instructions）」框的主提示词
- `knowledge/` —— 上传到 Gem 作为知识文件（共 5 个，Gem 上限 10 个）

## 部署到 Gemini Gems（约 5 分钟）
1. 打开 https://gemini.google.com → 左下角 **Gem manager（Gem 管理工具）**。
2. 点 **New Gem（新建 Gem）**，名称填：`港股招股章程数据复核助手`。
3. 打开本仓库 `gem-instructions.md`，**全文复制**粘贴到「指令」框。
4. 在 **Knowledge（知识）** 处，上传 `knowledge/` 下全部 5 个 `.md` 文件
   （如需，可另上传项目专属的定义词表、估值报告等，总数≤10 个）。
5. 用一段真实章节做 **Preview（预览）** 测试，确认输出为「结论摘要 + 疑点明细 + 未能验证项」三段式。
6. **Save（保存）**。之后在对话中选择该 Gem，把待核的章节文本/表格粘进去即可。

## 使用建议
- **分章节喂入**：招股章程很长，建议按 Financial Information、Business、Summary、
  Use of Proceeds 等分块复核，效果与可追溯性更好。
- **双语对照**：把英文版与中文版同一章节一并粘入，可触发第 4 步双语逐项核对。
- **表格复核**：把财务表格以文本/Markdown 形式粘入，便于 Gem 重算勾稽。
- **指定步骤**：可要求「只做第 2 步勾稽」或「只查中英文一致性」。

## 知识文件清单
| 文件 | 作用 |
|------|------|
| `knowledge/01-financial-tie-out.md` | HKFRS/IFRS 三表与跨表勾稽、指标重算公式 |
| `knowledge/02-consistency-and-bilingual.md` | 跨章节一致性 + 中英文双语逐项核对 |
| `knowledge/03-hkex-disclosure-checklist.md` | HKEX/App D1 披露要点与规范表述抽查 |
| `knowledge/04-proofreading-glossary.md` | 中英文校对、英式拼写、定义词规范 |
| `knowledge/05-common-errors.md` | 港股高频低级错误库与排查口诀 |
