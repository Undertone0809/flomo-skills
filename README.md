# flomo-skills

一个面向 Agent Skill 用户的 flomo 技能仓库。

这个仓库不是一个“大一统 flomo 框架”，而是三个边界清楚的独立 skill 集合：

- `flomo-local-api`
- `flomo-web-crud`
- `flomo-memo-to-markdown`

## 先看这个：我该用哪个 skill？


| 你的目标                                  | 推荐 skill                 | 为什么                                     |
| ------------------------------------- | ------------------------ | --------------------------------------- |
| 查 memo、总结最近在想什么、快速创建或编辑 memo          | `flomo-local-api`        | `mac` 用户默认首选，走本地登录态 + API，速度快很多         |
| 在真实 flomo Web 页面里操作 live account      | `flomo-web-crud`         | 不依赖官方 API，适合非 `mac` 用户，也适合本地 API 不可用时兜底 |
| 导出 Markdown、tag 统计、NotebookLM / AI 素材 | `flomo-memo-to-markdown` | 专门做导出与归档，不混入 CRUD 心智                    |


## 平台推荐

- `mac` 用户：默认优先 `flomo-local-api`
- 非 `mac` 用户：默认优先 `flomo-web-crud`
- 不管什么平台，只要目标是导出 Markdown：用 `flomo-memo-to-markdown`

## 三个 skill 的边界

### `flomo-local-api`

- 面向 `mac`
- 依赖本地 flomo 登录态
- 负责查询、总结、创建、编辑、tag 复用
- 不负责 live Web UI 自动化
- 不负责删除 memo



安装示例：

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-local-api
```

### `flomo-web-crud`

- 面向任意平台，尤其是非 `mac`
- 不依赖 flomo 官方 API
- 依赖 Chrome MCP 和已登录浏览器
- 负责 live Web UI 的 query / create / edit / delete
- 不是默认的高频查询入口，只有在 Web UI 场景或本地 API 不可用时优先使用



安装示例：

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-web-crud
```

### `flomo-memo-to-markdown`

- 面向导出、归档、NotebookLM、长文本 AI 消费
- 依赖本地 flomo 登录态和 API 读取能力
- 负责 Markdown 分片、tag 统计、附件处理
- 不承接“查找并修改一条 memo”这类交互



安装示例：

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-memo-to-markdown
```

## 仓库结构

```text
.agents/
  flomo-local-api/
  flomo-web-crud/
  flomo-memo-to-markdown/
```

每个 skill 都自带自己的文档、配置、脚本和 references。这个仓库故意不做 `shared/`，避免把三个用户任务重新耦合成一个抽象平台。