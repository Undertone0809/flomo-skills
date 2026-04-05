# flomo-web-crud

通过 Chrome MCP 操作真实 flomo Web UI 的技能。

## 适合什么场景

- 非 `mac` 用户需要查、建、改、删 flomo memo
- 必须操作真实浏览器里的 live flomo account
- 本地 API 路径不可用，需要 Web UI 兜底

## 不适合什么场景

- 想要最快速的高频查询或创建编辑，且你在 `mac` 上
- 只想做 Markdown 导出、tag 统计、NotebookLM 素材整理
- 不具备 Chrome MCP 和已登录浏览器环境

## 前置条件

- Chrome 已登录 flomo Web
- 当前 Agent 会话可用 Chrome MCP

## 安装

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-web-crud
```

## 最小验证

确认当前 Agent 环境至少能调用：

- `get_windows_and_tabs`
- `chrome_navigate`
- `chrome_read_page`

然后验证：

1. 能打开 `https://v.flomoapp.com/mine`
2. 能读到页面结构
3. 能在写操作前锁定 `memo_id`

更多细节看 [SKILL.md](./SKILL.md)。
