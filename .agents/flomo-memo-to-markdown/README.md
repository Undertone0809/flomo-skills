# flomo-memo-to-markdown

把 flomo memo 导出成按时间分组的 Markdown 文件和 tag 统计。

## 适合什么场景

- 想把 flomo 内容喂给 NotebookLM 或其他 AI 工具
- 想按月 / 季度 / 年拆分导出
- 想生成 `tag-stats.md`
- 想处理附件为 placeholder / ignore / copy 三种模式

## 不适合什么场景

- 查找并修改单条 memo
- live Web UI CRUD
- 本地 flomo 登录态不可用

## 前置条件

- `flomo.app` 曾在这台 `mac` 上登录过
- 当前环境能读取本地 flomo 登录态并访问 flomo API

## 安装

```bash
npx skills add Undertone0809/flomo-skills --skill flomo-memo-to-markdown
```

## 最小验证

```bash
SKILL_ROOT="${CODEX_HOME:-$HOME/.codex}/skills/flomo-memo-to-markdown"
SCRIPT="$SKILL_ROOT/scripts/flomo_to_nblm.py"
python3 "$SCRIPT" --preview-only
```

## 默认行为

- 默认走本地 flomo 登录态 + API
- 默认按月拆分
- 默认输出 Markdown 文件和 `tag-stats.md`
- 默认附件模式是 `placeholder`

更多细节看 [SKILL.md](./SKILL.md)。
