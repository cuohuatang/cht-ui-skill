# 工程化质量保障与图表选型参考（第 23 项）

> **推荐工程栈（去重后聚焦）**：质量保障用 **Storybook + Playwright** 双核心；图表用 **Recharts**（轻、React 原生、声明式，默认）打底，**ECharts** 仅在「复杂图表」时补充。
> 其余（Chromatic / axe-core / TS+zod / ESLint / Ant Design Charts / Visx）一律**非默认、按需**——见第三节「为什么不用其它」，避免泛泛罗列、重复包内已有能力。

---

## 一、推荐栈（头条，直接照着搭）

| 角色 | 工具 | 一句话定位 |
|------|------|-----------|
| 组件展示 / 状态沉淀 | **Storybook** | 每个 UI 组件单独陈列、对比，把 token 与状态矩阵（loading/empty/error）可视化 |
| 端到端验证 | **Playwright** | 模拟真实点击流程，验证关键路径（注册→下单→支付）跑得通不通 |
| 图表（默认） | **Recharts** | React 原生、声明式、上手快——Next.js 项目无缝，动效开箱即用 |
| 图表（补充） | **ECharts** | 图表最全、动效最丰富、中文社区强；**只在图表变复杂时用**（桑基/热力/地图/3D、强交互） |

### 落地要点（去重，只给推荐项 + 衔接）
- **Storybook**：组件库 / 设计系统必备；把第 6 项 `ui-ux-craft` 的 token 与状态矩阵在这里可视化沉淀，UI 是否统一、组件是否复用一眼可见。
- **Playwright**：落在第 12 项 `superpowers` 的「验证 / 测试」阶段——先 TDD 写单测，再用 Playwright 跑关键用户路径，替代手点回归。
- **Recharts**：默认选它。声明式组件直接嵌 JSX，无需额外封装；与第 20 项 `json-render` 的 React 渲染器天然兼容。
- **ECharts**：不要一开始上。当出现 Recharts 表达不了的复杂图表 / 强交互 / 需要中文文档时，再引入 `echarts-for-react` 做局部补充，避免全站混用两套图表体系。

---

## 二、图表选型决策（聚焦版）

| 你在做 | 用 |
|---|---|
| Next.js 项目要画图（默认、轻、React 友好） | **Recharts** |
| 图表变复杂：桑基 / 热力 / 地图 / 3D、强交互、要中文生态 | **ECharts**（作为 Recharts 的补充，局部引入） |
| 决定「什么数据用什么图」（事实层） | 第 21 项 `ui-ux-pro-max` 的「25 图表」知识库 |
| 把图表做成动效展示片 | 第 16 项 `design-to-motion`（仪表盘/图表被读、数据滚动入场） |
| AI 生成受控图表 UI | 第 20 项 `json-render` 的 catalog 护栏（声明允许的图表组件） |

---

## 三、为什么不用其它（去重说明）

以下**不是默认推荐**，仅在明确需要时考虑；它们的能力本包其它项已部分覆盖，故不重复展开：

- **Ant Design Charts / Visx**：企业后台报表风（AntD Charts）或有像素级定制需求（Visx）时才上；默认栈 Recharts 已覆盖 90% 场景，不要为「可能用到」提前引入。
- **Chromatic**（视觉回归）：配 Storybook 时在 CI 跑快照拦「改崩别的页」；属于 Storybook 的可选增强，非独立必选。
- **axe-core / jest-axe**（无障碍语义）：建议**保留作自动化底线**——它能查硬错误，第 19 项 `jakubkrehel-skills` 的 `better-accessibility` 与第 22 项 `hallmark` 的 **Floor 闸门**（对比度/focus/reduced-motion）补它查不到的「体验性无障碍」，两者叠加而非二选一。
- **TypeScript + zod**（前后端契约）：建议保留；与第 20 项 `json-render` 的 validation 护栏、第 6 项 `ui-ux-craft` 的 token 规范一致，边界处（API 响应/表单）做运行时校验。
- **ESLint 系列规则**：建议保留；配 design-token 规则拦「硬编码 `#3b82f6`、写死 14px」这类规范逃逸，对齐 `references/06-ui-ux-craft.md`。

> 一句话：**默认就 Storybook + Playwright + Recharts，复杂图表补 ECharts**；其余按需，不堆砌。
