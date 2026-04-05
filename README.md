# flomo-skills

Production-ready flomo skills for agent workflows.

这个仓库不是一个“大一统 flomo 框架”，而是三个边界清楚、面向真实使用场景的独立 skill：

- `flomo-local-api`
- `flomo-web-crud`
- `flomo-memo-to-markdown`

适合放进 `skills` 生态，按任务安装，按平台选择。

## Why this repo

flomo 相关自动化其实有三种完全不同的工作方式：

1. 本地登录态 + API，适合高频查询和轻写入
2. 真实 Web UI 自动化，适合 live account 操作
3. Markdown 导出与归档，适合 AI / NotebookLM / 长文本消费

把它们硬塞进一个 skill，最后只会变成一个又慢又混乱的入口。

这个仓库的目标很直接：

- `mac` 用户默认走更快的 `flomo-local-api`
- 非 `mac` 用户默认走 `flomo-web-crud`
- 导出场景单独走 `flomo-memo-to-markdown`

## Choose the right skill

| 你的目标 | 推荐 skill | 适合谁 | 为什么 |
| --- | --- | --- | --- |
| 查 memo、总结最近在想什么、快速创建或编辑 memo | `flomo-local-api` | `mac` 用户 | 走本地登录态 + API，速度快很多，适合日常高频使用 |
| 在真实 flomo Web 页面里操作 live account | `flomo-web-crud` | 任意平台，尤其非 `mac` | 不依赖官方 API，直接复用已登录浏览器 |
| 导出 Markdown、tag 统计、NotebookLM / AI 素材 | `flomo-memo-to-markdown` | `mac` 用户 | 专门做导出与归档，不把 CRUD 和导出混成一团 |

## Typical cases

这几个 case 基本覆盖了大多数真实使用场景：

| Case | 应该用哪个 skill | 原因 |
| --- | --- | --- |
| “帮我看看最近 30 天我在反复写什么” | `flomo-local-api` | 这是查询 + 总结，不需要 Web UI |
| “把这条 flomo memo 改掉，或者直接删掉” | `flomo-web-crud` | 这是 live account 操作，尤其删除必须走明确的 Web UI 路径 |
| “导出 2025 年的 memo，按季度拆分，给 NotebookLM 用” | `flomo-memo-to-markdown` | 这是标准导出场景，不该走 CRUD skill |
| “我在 Windows 上，只想查几条 flomo memo” | `flomo-web-crud` | 非 `mac` 默认走 Web UI |
| “我在 Mac 上高频写 memo，还想复用已有 tag” | `flomo-local-api` | 本地 API 更快，也更适合 tag reuse 工作流 |
| “我想把 flomo 当成长期知识输入源喂给 AI” | `flomo-memo-to-markdown` | 这类需求的核心是稳定导出和 tag 统计 |

## Platform guidance

- `mac` 用户：默认优先 `flomo-local-api`
- 非 `mac` 用户：默认优先 `flomo-web-crud`
- 不管什么平台，只要目标是导出 Markdown：用 `flomo-memo-to-markdown`

## Installation

先装你真正需要的 skill。没必要一口气装全部。

### Install `flomo-local-api`

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-local-api
```

### Install `flomo-web-crud`

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-web-crud
```

### Install `flomo-memo-to-markdown`

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-memo-to-markdown
```

如果你只是想先确认远端仓库能被识别，可以先跑：

```bash
npx skills add https://github.com/Undertone0809/flomo-skills --list --full-depth
```

## Skill details

### `flomo-local-api`

- 面向 `mac`
- 依赖本地 flomo 登录态
- 负责查询、总结、创建、编辑、tag 复用
- 不负责 live Web UI 自动化
- 不负责删除 memo

入口：
- [README.md](./.agents/flomo-local-api/README.md)
- [SKILL.md](./.agents/flomo-local-api/SKILL.md)

### `flomo-web-crud`

- 面向任意平台，尤其是非 `mac`
- 不依赖 flomo 官方 API
- 依赖 Chrome MCP 和已登录浏览器
- 负责 live Web UI 的 query / create / edit / delete
- 不是默认的高频查询入口，只有在 Web UI 场景或本地 API 不可用时优先使用

入口：
- [README.md](./.agents/flomo-web-crud/README.md)
- [SKILL.md](./.agents/flomo-web-crud/SKILL.md)

### `flomo-memo-to-markdown`

- 面向导出、归档、NotebookLM、长文本 AI 消费
- 依赖本地 flomo 登录态和 API 读取能力
- 负责 Markdown 分片、tag 统计、附件处理
- 不承接“查找并修改一条 memo”这类交互

入口：
- [README.md](./.agents/flomo-memo-to-markdown/README.md)
- [SKILL.md](./.agents/flomo-memo-to-markdown/SKILL.md)

## Repository layout

```text
.agents/
  flomo-local-api/
  flomo-web-crud/
  flomo-memo-to-markdown/
```

每个 skill 都自带自己的文档、配置、脚本和 references。这个仓库故意不做 `shared/`，因为这三个能力的用户任务边界本来就不同，强行抽象只会让入口变差。

## Discoverability

这个仓库已经可以被 `skills` CLI 发现。公开仓库被正常安装后，也会逐步进入 [skills.sh](https://skills.sh/) 的可发现路径。
