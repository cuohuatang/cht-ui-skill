# ponytail —— 嫁接说明（cht-ui-skill 第 25 项）

> 上游：`DietrichGebert/ponytail`（⭐ ~194k，MIT，v5.3.3，2026-10-29）
> 定位：专治 AI 写代码过度设计的 Agent Skill——「扎马尾的老程序员」模式，YAGNI 决策阶梯。

## 嫁接范围（curated 精选，39 文件 / ~174KB）

- **规则主文件**：`AGENTS.md`（懒人高级工程师完整规则）、`.cursor/rules/ponytail.mdc`（always-on 规则，与 .clinerules/.windsurf/.kiro/.qoder/.agents 6 份拷贝同文，去重只收此份）
- **命令 SKILL**：`skills/`（ponytail 主技能 + review/audit/debt/gain/help 5 命令）、`commands/`（6 个 Codex toml）
- **文档**：`README.md`、`INSTALL.md`（14+ 宿主安装路径）、`docs/agent-portability.md`（20 家 Agent 适配映射）、`i18n/README.zh-CN.md`（中文版）
- **案例**：`examples/`（12 个 before/after：日期选择器 335→10 行、防抖、限流、邮箱校验…）
- **基准**：`benchmarks/README.md` + `benchmarks/results/2026-10-07-agentic.md`（v5：-53% 代码 / -41% 耗时 / -26% 成本 / -45% token，6 项安全任务 30/30 全过）与 `2026-06-18-agentic.md`（v4 基准：-54% 代码 / -22% token / -20% 成本 / -27% 耗时，安全 100%）
- **元信息**：`LICENSE`、`package.json`、`.claude-plugin/plugin.json`、`.codex-plugin/plugin.json`

## 有意跳过

`assets/`（11MB 图片画廊）、`tests/`、`hooks/`（20 文件运行层 Node 脚本与 UI 面板 band/ ——真实宿主安装走 `/plugin marketplace add DietrichGebert/ponytail` + `/plugin install ponytail@ponytail` 即获得完整运行层）、`benchmarks/` 脚本（run.py/tasks.py 等）、`.openclaw/`、`.opencode/`、`.agents/` 等镜像拷贝、i18n es/ja/ko、根 `__init__.py`。

## 核心：六步决策阶梯（动手前依次停在第 1 个站得住的档）

1. **这功能需要存在吗？** → 没人要的特性/选项/灵活性，跳过，并用一行点名
2. **代码库已有？**（helper/组件/服务/模式）→ 按周边代码的用法复用
3. **标准库/平台能力够吗？** → 用原生（`input type=date` 而非装日历库）；项目自有组件优先于原生
4. **已装依赖能覆盖吗？** → 用现有依赖，绝不为几行代码加包
5. **能一行写完且一眼读懂吗？** → 一行
6. **都不行：** 写能工作的最小实现

**永不削减**：信任边界的校验、防数据丢失的错误处理、安全、无障碍、真实硬件所需校准、用户明确要的东西。代码变短是因为必要，不是 golf。

## 四档强度与常用命令

| 级别 | 行为 |
|---|---|
| lite | 按要求实现，但用一行话点出更懒的替代方案，由用户决策 |
| **full（默认）** | 严格执行决策阶梯：标准库与原生优先、最短 diff |
| ultra | YAGNI 极端：先质疑需求本身再动手（慎用于产品场景） |
| off | 关闭规则注入 |

`/ponytail [mode]` 切换 · `/ponytail-review` 审查当前 diff 出可删清单 · `/ponytail-audit` 全库过度工程审计 · `/ponytail-debt` 收拢 `ponytail:` 注释捷径成台账 · `/ponytail-gain` 基准成绩板 · `/ponytail-help` 速查
