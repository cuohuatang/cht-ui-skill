# taste-skill（cht-ui-skill 第 14 项 · 精选嫁接）

来源：[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)（⭐ ~112k，v2.5.1，Apache-2.0 风格，作者 Leonxlnx）。

> **精选嫁接说明**：上游仓库是 35 MB / 1631 文件的设计工作室级技能包（含数百个 SVG 图标、webp/照片画廊、scene/object 二进制素材）。本目录只收**知识与方法层**，保持 cht-ui-skill 精简：
> - ✅ 收录：`SKILL.md`（主指令）、`library/`（palettes / type 蓝图）、`references/`（反 slop 房规、sections、copy、photos、moments、effects、gate 等实质文档）、`scripts/`（Node 实测工具：inspect / draw / gate / start / photos / moments / perf / icons / effects / copy-lint / consistency）。
> - ❌ 省略：上游 `assets/` 下的二进制画廊（icons / photos / scenes / objects / ui / backgrounds / components / moments / effects / diagrams 及 system.css·js·starter.html）。这些是演示素材，**不影响设计判断知识**。
> - 🔧 运行 `scripts/` 需要上游完整 `assets/` 与 Node 22 + Chrome/Chromium（ffmpeg 可选）。本目录的脚本作为「方法参考」保留；要真正跑浏览器实测循环，请取上游完整技能。

## 功能作用（读懂它）
tasteskill 是「给编码 Agent 的审美」：把"页面像不像 AI 生成"从形容词变成可执行的房规与方法。核心是：
- **九条房规（House rules）** 压过一切：图下不写说明、每个视觉在 1440/1024/768/390 都渲染、一屏一节、左右等边、hover 微动、多用真实照片、真实全彩图标、技术类页面才上 shader 场景、地址只写到街区。
- **页面类型驱动**：software / gaming / tech / product / service / place 六类，各自决定"上不上特效、照片怎么排、文案密度"。
- **真实浏览器实测**：`scripts/inspect.mjs` 量排版、`draw.mjs` 发牌研究方向、三宽度截图 → rubric → fix 的 look-and-fix 循环；`gate.mjs` 是提交前的 finish gate。
- **研究方向引擎**：从 247 个策展画廊站提炼的方向、`library/` 给出 type/palette/section 蓝图。

与 cht-ui-skill 的关系：frontend-design 给审美立场 → taste-skill / garden-skills 给方向素材与实测验收 → impeccable 给改稿动词与客观评审，三者共同治「AI 味 / 模板脸」。
