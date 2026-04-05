# flomo-local-api

本地 flomo 登录态 + API 路径的高频技能。

## 适合什么场景

- 在 `mac` 上查 memo、按 tag 搜索、做最近状态总结
- 快速创建或编辑 memo
- 先复用已有 tag，再写入内容
- 想要比 Web UI 自动化更快、更稳的体验

## 不适合什么场景

- 删除 memo
- 必须通过真实 flomo Web 页面操作 live UI
- 非 `mac` 环境或本地 flomo 登录态不可用

## 前置条件

- `flomo.app` 曾在这台 `mac` 上登录过
- 本地登录态仍然存在于 `~/Library/Containers/com.flomoapp.m/...`

## 安装

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-local-api
```

## 最小验证

```bash
SKILL_ROOT="${CODEX_HOME:-$HOME/.codex}/skills/flomo-local-api"
SCRIPT="$SKILL_ROOT/scripts/flomo_local_api.py"
python3 "$SCRIPT" query --days 7 --limit 3 --format markdown
```

## 主要能力

- `query`: 按关键词、tag、时间范围查 memo
- `summarize`: 总结最近在想什么
- `tags`: 先看用户已有 tag 体系，再做写入
- `create`: 创建纯文本 memo
- `edit`: 按 slug 或 flomo URL 编辑现有 memo

更多细节看 [SKILL.md](./SKILL.md)。
