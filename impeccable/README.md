# impeccable（cht-ui-skill 第 18 项 · 精选嫁接）

来源：[pbakaus/impeccable](https://github.com/pbakaus/impeccable)（⭐ ~106k，v4.8.1，Apache-2.0，作者 pbakaus）。

> **精选嫁接说明**：上游仓库是 85 MB / 4469 文件（含 Rust 检测器引擎、563KB `live-browser.js`、1.1MB `font-index.json`、tests / ui / vscode 等）。本目录只收**人读词汇、指令 playbook 与规则文档**，保持 cht-ui-skill 精简且可直接阅读：
> - ✅ 收录：`SKILL.md`（主指令，v4.8.1）、`reference/`（24 条指令各自的 playbook：bolder/quieter/distill/critique/audit/polish/harden/clarify/adapt/onboard/optimize/generate/document/extract/init/live/shape/animate/delight/overdrive/typeset/layout/colorize… 及 `critique.md`/`audit.md`/`craft-floor.md` 等确定性 slop 检测器与绝对禁令文档）、`scripts/command-metadata.json`（指令与规则清单）。
> - ❌ 省略：Rust 二进制引擎 `scripts/impeccable`、563KB `live-browser.js`、1.1MB `font-index.json`、tests / ui / vscode / `.agents` 镜像目录。
> - 🔧 真正运行 `critique`/`audit` 检测器需要上游的自包含二进制引擎；本目录提供的是**改稿动词与客观评审的方法与规则文檔**，可直接当评审清单使用。

## 功能作用（读懂它）
impeccable 是「给编码 Agent 的设计词汇表」：用**可命名的指令**代替"make it pop"这类模糊诉求，并用**确定性检测器（62 条反-slop 规则）**在交付前拦下 AI 味。核心是：
- **24 条改稿指令**：`bolder`(放大稳妥) / `quieter`(压低过响) / `distill`(删多余) / `colorize` / `typeset` / `layout` / `animate` / `delight` / `overdrive` / `critique`(打分 UX 评审) / `audit`(P0–P3 技术质量) / `polish` / `harden`(边界/错误/i18n/溢出) / `clarify` / `adapt` / `optimize` / `onboard` / `live` / `generate` / `shape` / `init` / `document` / `extract`。
- **62 条确定性 slop 规则**：无 LLM、无 API key 地标记 AI 默认陷阱（Inter 包打一切、紫蓝渐变、卡片套卡片、灰字压彩底、标题上方圆角图标瓦片、cramped padding、跳级标题…）。规则文档见 `reference/critique.md`、`reference/audit.md`、`reference/craft-floor.md`（绝对禁令 + 检测器抓不到的反射动作）。
- **四种 Mode**：Persuade / Operate / Read / Experience，按访客成功方式缩放设计野心。

与 cht-ui-skill 的关系：frontend-design 给审美立场 → taste-skill 给方向素材与实测 → **impeccable 给改稿动词与客观评审闭环**，三者共同把"像不像 AI"从感觉变成动词与可勾选的规则。
