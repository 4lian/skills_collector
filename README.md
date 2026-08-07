# skills_collector

收集用于**弥补 AI 审美 / 动效缺陷**的 coding-agent skill（Claude Code / Codex / Cursor / WorkBuddy 通用的 `SKILL.md` 格式）。全部收编在 `ui/` 目录下。

## 为什么有这个仓库

AI 写 UI 的三大通病：

1. **一眼假的"AI 味"**——紫蓝渐变背景 + 圆角卡片 + 白色大字 + 廉价 emoji 图标。
2. **动效全靠临场发挥**——各组件动画风格不统一，节奏散了。
3. **动画性能稀烂**——layout thrashing、blur 滥用、没有 `prefers-reduced-motion`。

本仓库把社区里真正能治这些毛病的 skill 按角色分层收编，免得每次从头搜、从头踩坑。

---

## 总览对比

| # | Skill | 来源 / 星标 | 角色 | 动效相关度 | 体积(文件) | 一句话定位 |
|---|-------|------------|------|:----------:|:----------:|-----------|
| 1 | `frontend-dev` | 本机私有 (WorkBuddy) | 全能前端工作室 | 中 | 100(含54字体) | 设计+动效+素材+文案一体机 |
| 2 | `frontend-design` | Anthropic 官方 | 审美地基 | 间接 | 2 | 强制定调性，禁 AI 味字体 |
| 3 | `taste-skill` | Leonxlnx · 68.7K★ | 反 Slop 设计总监 | 中 | 15 | 人格变体 + GSAP 动效骨架 |
| 4 | `ui-ux-pro-max` | nextlevelbuilder · 84.9K★ | 可检索规则库 | 中 | 44 | 84 风格 / 192 配色 / 16 GSAP 预设 |
| 5 | `impeccable` | pbakaus (Apache-2.0) | 完整 UI 工作流 | 中 | 147 | 23 命令，animate/bolder/delight |
| 6 | `ui-skills` | ibelick · 4K★ | 注册中心 + 路由 | 中 | 9 | 按 motion/a11y 路由到子 skill |
| 7 | `gsap-skills` | GreenSock 官方 (MIT) | 动画执行层 | 强 | 9 | 8 模块，别让 AI 编 GSAP |
| 8 | `transitions-dev` | Jakubantalik · 2.2K★ | CSS 过渡库 | 强 | 32 | 27 个即贴即用的 `t-*` 过渡 |
| 9 | `animation-micro-interaction-pack` | majiayu000 (MIT) | 微交互预设 | 强 | 1 | hover/entrance/gesture 模式 |
| 10 | `emil-skills` | emilkowalski · 22.2K★ | 克制动效打磨 | 强 | 14 | 该不该动 / 用什么缓动 |
| 11 | `design-motion-principles` | kylezantos | 动效双模式 | 强 | 15 | 创建 + 审计，三派加权 |
| 12 | `motion` | Sagargupta16 · 80分 | 三模式审计 | 强 | 4 | 迪士尼 12 原则 / file:line |
| 13 | `interaction-design` | secondsky (MIT) | 交互模式 | 强 | 1 | loading/error/empty + a11y |
| 14 | `web-design-guidelines` | Vercel | 质量门禁 | 间接 | 1 | 生成后审计 a11y/性能/UX |
| 15 | `extract-design-system` | arvindrk | Token 提取 | 间接 | 3 | 抄真站的色/字/比例 token |

> 星标取自各源仓库 / registry 的 2026 年公开数据，可能变动；"动效相关度"为本仓库主观评级（强=直接教动画/动效，中=含动效但更泛设计，间接=门禁/提取/基调）。

---

## 角色分层与详解

### A. 地基 / 基调（先装这两个，否则后面都是空中楼阁）

- **`frontend-design`**（Anthropic 官方）：约 400 token 的 `SKILL.md`，强制 AI **先定审美方向再写码**，并禁用 Inter / Roboto / Arial / Space Grotesk 这些"AI 味字体"。是一切的起点。
- **`frontend-dev`**（本机 WorkBuddy）：全能工作室。反模板底子——NEVER 用 Inter（强制 Geist/Outfit/Satoshi）、NEVER AI 紫蓝、VARIANCE>4 时禁止居中 Hero、动效工具矩阵（Framer Motion / GSAP / Three.js）+ 性能护栏（`transform`/`opacity` 优先、`useEffect` 必须 `ctx.revert()` 清理）。已内置 54 个字体，开箱即用。

### B. 设计总监 / 审美系统

- **`taste-skill`**：反 Slop 前端框架。三旋钮（`DESIGN_VARIANCE` / `MOTION_INTENSITY` / `VISUAL_DENSITY`）调气质；含 minimalist / brutalist / soft / brandkit / redesign / image-to-code 等人格变体 + GSAP 动效骨架。
- **`ui-ux-pro-max`**：可检索本地规则库（Python 脚本 + CSV）。84 风格 / 192 配色 / 74 字体配对 / **16 个 GSAP motion presets** / 22 技术栈。要花样多就它。
- **`impeccable`**：完整 UI 工作流（23 命令、44 检测规则、品牌/产品模式分离、实时浏览器迭代）。argument-hint 含 `animate` / `bolder` / `delight` / `overdrive` 等动效模式。
- **`ui-skills`**：设计工程师 skill 注册中心 + CLI，按 motion / accessibility / typography 维度自动路由到最匹配的子 skill（含 `fixing-motion-performance`、`improve-ui`）。本质是"让 agent 找到对的 UI skill"的分发机制。

### C. 动效执行（直接出动画代码）

- **`gsap-skills`**（GreenSock 官方）：8 模块——core / timeline / scrolltrigger / plugins / react / frameworks / performance / utils。价值：把滚动动画、React cleanup、ScrollTrigger refresh 等坑变成规则，AI 不再 hallucinate GSAP。Webflow 收购后 GSAP 全插件免费。
- **`transitions-dev`**：27 个开箱即用 CSS 过渡（dropdown / modal / toast / skeleton / accordion…），统一 `t-*` 命名空间 + CSS 变量 + `prefers-reduced-motion` 降级；自带 `reveal` / `apply` / `review` / `refine` 命令。
- **`animation-micro-interaction-pack`**：纯 `SKILL.md`。hover / entrance / exit / loading / gesture 模式 + Tailwind 动画 + Framer Motion 示例 + best practices（200–300ms，reduced-motion）。

### D. 动效打磨 / 审计（让动效"高级"且不过度）

- **`emil-skills`**（Emil Kowalski 哲学，Vercel/Linear 御用）：`emil-design-eng` 主技能 + `animate` / `animation-vocabulary` / `improve-animations` / `review-animations` 等。核心：该不该动、用什么缓动、多快——克制的高级感。
- **`design-motion-principles`**：双模式 **Create**（构建）+ **Audit**（审计，输出品牌化 HTML 报告带循环 demo）。整合 Emil Kowalski（克制）/ Jakub Krehel（生产打磨）/ Jhey Tompkins（创意实验）三派，按项目上下文加权。内置 anti-AI-slop 动效检查表（pulsing indicator、hover-scale-on-everything、stagger-spam…）。
- **`motion`**：三模式 **audit**（迪士尼 12 原则，`file:line` 找问题）/ **add** / **fix**（性能：layout thrashing、compositor 属性、scroll-linked、blur）。
- **`interaction-design`**：反馈模式 + 微交互 + 可访问交互（loading / error / empty states），动画指南（<500ms，ease-out 进入，reduced-motion）。

### E. 验证 / 门禁 / 提取

- **`web-design-guidelines`**（Vercel）：生成后审计 UI 是否符合 Web Interface Guidelines（a11y / 性能 / UX）。和生成类技能绝配。
- **`extract-design-system`**：headless 渲染真实网站，导出颜色 / 字体 / 比例 token 文件，用作项目起点（"抄作业但抄得有理"）。

---

## 推荐组合（按场景）

**场景 1 · 从零做一个漂亮落地页 / 营销站**
`frontend-design`（定调）→ `frontend-dev` 或 `taste-skill`（落地）→ `gsap-skills` + `transitions-dev`（动效）→ `web-design-guidelines`（审计）

**场景 2 · 给现有 App 统一加动效（不打架）**
`design-motion-principles`（审计现状 + 定权重）→ `motion` 或 `emil-skills`（打磨）→ `transitions-dev`（即贴即用过渡）

**场景 3 · 要最多的风格 / 配色 / 字体花样**
`ui-ux-pro-max`（检索规则库）→ `impeccable`（落地 + 迭代）

**场景 4 · 避免 AI 动效臭味**
`design-motion-principles`（anti-AI-slop 检查表）+ `motion`（audit 模式）

**场景 5 · WorkBuddy 本机直接用**
`frontend-dev` 已在 `~/.workbuddy/skills/`，无需安装；其余按需复制。

---

## 安装（通用）

这些都是标准 `SKILL.md` 格式，复制到对应 agent 的 skills 目录即可：

- **Claude Code / Codex**：`~/.claude/skills/<skill-name>/`（Windows: `%USERPROFILE%\.claude\skills\`）
- **Cursor**：`~/.cursor/skills/`
- **WorkBuddy**：`~/.workbuddy/skills/`（用户级）或 `{项目}/.workbuddy/skills/`（项目级）

示例（以 `taste-skill` 为例，它是"全家桶"，复制整个目录）：

```bash
cp -r ui/taste-skill ~/.claude/skills/taste-skill
```

> 注意：`ui/taste-skill/`、`ui/emil-skills/`、`ui/ui-skills/` 都是"全家桶"——下含多个子技能（如 `taste-skill` 含 minimalist-skill、brutalist-skill…；`emil-skills` 含 emil-design-eng、animate、review-animations…）。按需取用或整体安装。

---

## 选型决策树（一句话版）

- 要"AI 别画那么丑"的地基 → **`frontend-design`**
- 要一个全能工作室开箱落地 → **`frontend-dev`**
- 要特定人格（极简 / 粗野 / 高端柔）或逆向抄站 → **`taste-skill`**
- 要花样最多的规则库 → **`ui-ux-pro-max`**
- 要动画代码别写错 → **`gsap-skills`**
- 要即贴即用的过渡 → **`transitions-dev`**
- 要动效"高级且不 AI 味" → **`emil-skills` / `design-motion-principles` / `motion`**
- 要生成后审计 → **`web-design-guidelines`**

---

## 同步 / 更新（Sync）

本仓库是 **vendoring 快照**：每个 skill 是整目录拷进来的，丢了 git 血缘。上游一升级，不会自动跟着动。所以配套了"族谱 + 脚本"来手动/定时同步。

### 机制
- **`sync-manifest.json`** —— 每个 skill 的"族谱"：上游仓库 `repo`、要取的子目录 `subpath`、目标路径 `target`、来源类型 `source`（github / local）。
  - `frontend-dev` 标记为 `local`（本机 WorkBuddy 私有，无上游，只在本机副本变化时刷新）。
  - 其余 14 个都记了真实 GitHub 仓库 + 提取路径（很多来自 monorepo 的子目录，比如 `anthropics/skills` 里的 `skills/frontend-design`）。
- **`sync.py`** —— 按谱执行同步：
  1. GitHub 项用 **sparse-clone**（`--filter=blob:none --sparse`）只拉 `subpath` 子目录，不把整个大 monorepo / 大 registry 搬下来；
  2. 自动解析上游默认分支（`git ls-remote --symref`）；
  3. 覆盖拷贝到 `ui/<target>/`，自动排除 `.git` / `__MACOSX` / `.DS_Store`；
  4. 把上游 commit sha 记进 **`sync-state.json`**，下次跑能判断"是否真有更新"；
  5. 默认只更新工作区并打印报告；带 `--push` 才提交推送。
- **`_sync/`** 是临时克隆目录（已 gitignore，不会进仓库）。

### 用法
```bash
# 1) 只更新工作区 + 看报告（不提交）
python sync.py

# 2) 更新并直接提交 + 推送
python sync.py --push

# 3) 只同步某一个（改 manifest 临时注释其他，或手动跑）
```
> 要求：环境能走 SSH 推 GitHub（已配 `id_ed25519`），且能访问 github.com:22。

### 定时自动同步
仓库挂了一个**每周自动化**：自动 `git pull` → `python sync.py --push` → 报告哪些 skill 升级了。可在 WorkBuddy 自动化设置里改频率（比如改每月、或换成手动触发）。

### 已知取舍
- 同步是"上游覆盖本地"——如果你在仓库里手改过某个 skill，再 sync 会被上游覆盖（vendoring 的代价）。要本地改，请 fork 上游或另建分支。
- 上游**删掉**的文件不会从 `ui/` 里自动移除（沙箱 safe-delete 禁止 rm，且保留无害）。极少情况下如需彻底对齐，手动删一次即可。
- `animation-micro-interaction-pack` 上游是 `majiayu000/claude-skill-registry`（大仓库），靠 sparse-checkout 只取 `skills/data/animation-micro-interaction-pack`。

---

*本仓库仅作聚合与本地存档。各 skill 版权归原作者，license 见各自 `SKILL.md` / 源仓库。*
