# flomo-skills

Production-ready flomo skills for agent workflows.

这个仓库提供 3 个可独立安装的 flomo agent skills。

**一句话选技能：**
- **Mac 用户** → 装 `flomo-local-api`（功能最全，体验最好）
- **Windows 用户** → 装 `flomo-web-crud`（通过浏览器操作）
- **需要导出 Markdown** → 装 `flomo-memo-to-markdown`

---

## Quick Start

### Mac 用户（推荐）

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-local-api
```

Mac 用户只需要这一个技能就够了。它覆盖了查询、创建、编辑、总结等所有常用操作，而且比 Web 自动化更快更稳。

### Windows 用户

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-web-crud
```

Windows 上通过 Chrome MCP 操作浏览器完成 CRUD。

### 需要导出 Markdown？

无论哪个平台，导出功能都是独立的：

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-memo-to-markdown
```

---

## 功能对比

| 功能 | `flomo-local-api` (Mac) | `flomo-web-crud` (Windows) |
|------|------------------------|---------------------------|
| 查询 memo | ✅ | ✅ |
| 创建 memo | ✅ 智能复用已有 tag | ✅ |
| 编辑 memo | ✅ | ✅ |
| 删除 memo | ❌ | ✅ |
| 总结/分析 | ✅ | ✅ |
| tag 统计 | ✅ | ✅ |
| 速度 | 快（直接 API）| 较慢（浏览器自动化）|
| 稳定性 | 高（不依赖 UI）| 中（依赖页面元素）|

**关键区别：** `flomo-web-crud` 能做的，`flomo-local-api` 在 Mac 上基本都能做，而且做得更好。唯一的例外是”删除 memo”——出于安全考虑，`flomo-local-api` 不提供删除功能。

---

## 为什么 Mac 用户应该选 `flomo-local-api`

### 1. 更快

直接走本地登录态 + 官方 API，不需要打开浏览器、等待页面加载、模拟点击。查一条 memo 是毫秒级响应，不是秒级。

### 2. 更稳

不依赖 DOM 结构，不会因为 flomo 改版、按钮位置调整、弹窗变化而崩溃。API 是稳定的契约，UI 是易变的实现。

### 3. 智能 tag 复用

这是 `flomo-local-api` 的杀手级特性。

当你创建 memo 时，它会先扫描你历史上用过的所有 tag，分析你的标签体系，然后**优先建议已有标签**。而不是像 Web 自动化那样直接写入，导致标签越来越乱。

**长期价值：** 半年后你的 tag 体系依然清晰可检索，不会因为 AI 随手造了一堆 `#思考` `#think` `#thinking` 而失控。

### 4. 更适合高频使用

日常查询、快速记录、总结最近想法——这些高频动作走 API 才是合理的。把浏览器自动化留给真正需要可视化确认的场景（比如删除）。

---

## 使用场景指南

| 你想做什么 | 推荐技能 | 说明 |
|-----------|---------|------|
| “帮我看看最近 30 天我在反复写什么” | `flomo-local-api` | 查询 + 总结是 API 的强项 |
| “快速记一条 memo，沿用我现有的 tag” | `flomo-local-api` | 智能 tag 复用，不乱造新标签 |
| “删掉某条 memo” | `flomo-web-crud` | 删除操作走浏览器更稳妥 |
| “把 2025 年 memo 导出给 NotebookLM” | `flomo-memo-to-markdown` | 独立导出技能 |
| “分析我的 tag 使用情况” | `flomo-local-api` | 自带 tag 统计 |

---

## 技能详情

### `flomo-local-api`（Mac 主力技能）

功能：查询、创建、编辑、总结、tag 分析

特色：
- 走本地登录态 + API，毫秒级响应
- **智能 tag 复用**：写入时优先建议已有标签，维护标签体系整洁
- 不支持删除（出于安全考虑，删除请走 Web UI）

[查看 SKILL.md →](./.agents/flomo-local-api/SKILL.md)

### `flomo-web-crud`（Windows / 浏览器方案）

功能：查询、创建、编辑、**删除**

特色：
- 通过 Chrome MCP 操作浏览器
- 不依赖官方 API，任何平台可用
- 适合 Windows 用户或必须删除 memo 的场景

[查看 SKILL.md →](./.agents/flomo-web-crud/SKILL.md)

### `flomo-memo-to-markdown`（导出专用）

功能：Markdown 导出、tag 统计、附件处理

特色：
- 按时间范围导出，支持切分大文件
- 生成 NotebookLM 友好的格式
- 独立的归档技能，不是 CRUD 附属

[查看 SKILL.md →](./.agents/flomo-memo-to-markdown/SKILL.md)

---

## 仓库结构

```text
.agents/
  flomo-local-api/      # Mac 主力技能
  flomo-web-crud/       # Windows / 浏览器方案
  flomo-memo-to-markdown/  # 导出专用
```

每个 skill 自带 `SKILL.md`、配置和脚本。根 README 是唯一入口，避免文档分散。

---

## 验证安装

确认仓库能被 `skills` CLI 正常识别：

```bash
npx skills add https://github.com/Undertone0809/flomo-skills --list --full-depth
```

公开仓库安装后会逐步进入 [skills.sh](https://skills.sh/) 的可发现路径。
