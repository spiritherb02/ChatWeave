# ChatWeave

跨平台 AI 聊天记录迁移工具。把 ChatGPT、DeepSeek、Grok、Qwen 等平台的聊天记录导出后，整理并合并为 RikkaHub 可导入的备份包。所有处理在浏览器本地完成，数据不上传服务器。

## 开始使用

**推荐在线访问：** https://cw.spiritherb.top

> 始终部署最新版本，无需手动下载更新。也可以下载 `index.html` 本地打开，功能完全一致。

## 已支持的导出来源

- ChatGPT 官方导出 ZIP
- DeepSeek 新版导出 ZIP（含工具调用、搜索结果、再生分支、编辑消息变体）
- DeepSeek 旧版导出 ZIP（chat.csv / coder.csv）
- Grok 官方导出 ZIP（prod-grok-backend.json）
- Qwen 官方导出 JSON（chat.qwen.ai）
- YourAIScroll / ChatWeave Exporter 导出的 JSON
- Markdown 粘贴导入

## 工作流程

```
导入 → 预览（支持消息变体 ◀▶ 切换、思考链/工具调用独立卡片）→ 勾选 → 合并 → 下载 RikkaHub 备份
```

## 组件

| 文件/目录 | 说明 |
|---|---|
| `index.html` | 主工具：导入 → 预览/勾选 → 合并 → 下载 RikkaHub 备份 |
| `edge_exporter_lite/` | 浏览器扩展：在 AI 聊天页面上一键提取当前会话，导出为 JSON/Markdown/文本/HTML |
| `sync_version.js` | 版本同步脚本：一键同步 `index.html`、`manifest.json`、`popup.js` 的版本号 |
| `chatweave-version.json` | 唯一版本号来源 |
| `wrangler.jsonc` | Cloudflare Workers 部署配置 |

## 版本管理

```bash
# 查看当前版本
node sync_version.js

# 更新版本号并同步所有目标
node sync_version.js 1.8.0
```

## 浏览器扩展

`edge_exporter_lite/` 是 Chrome/Edge 扩展源码。在支持平台（DeepSeek、ChatGPT 等）的聊天详情页打开扩展弹窗，即可提取当前会话。

## 隐私

所有数据处理在浏览器本地完成，不经过服务器。合并前请保留原始导出文件和 RikkaHub 备份，确认无误后再删除。

## 链接

- 在线使用：https://cw.spiritherb.top
- GitHub：https://github.com/spiritherb02/ChatWeave
- RikkaHub：https://rikka-ai.com
