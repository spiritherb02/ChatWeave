# ChatWeave

跨平台 AI 聊天记录迁移工具。把 ChatGPT、DeepSeek、Grok、Qwen 等平台的聊天记录导出后，整理并合并为 RikkaHub 可导入的备份包。所有处理在浏览器本地完成。

## 组件

| 文件/目录 | 说明 |
|---|---|
| `index.html` | 主工具：导入 → 预览/编辑/勾选 → 合并 → 下载 RikkaHub 备份 |
| `edge_exporter_lite/` | 浏览器扩展：在 AI 聊天页面上一键提取当前对话，导出为 JSON/Markdown/文本/HTML，优先走 API 提取，失败自动回退页面解析 |
| `sync_version.js` | 版本同步脚本：一键同步 `index.html`、扩展 `manifest.json`、`popup.js` 的版本号 |
| `chatweave-version.json` | 唯一版本号来源 |
| `wrangler.jsonc` | Cloudflare Workers 部署配置 |

## 已支持的导出来源

- ChatGPT 官方导出 ZIP
- DeepSeek 新版导出 ZIP（含工具调用、搜索结果、重新生成分支）
- DeepSeek 旧版导出 ZIP（chat.csv / coder.csv）
- Grok 官方导出 ZIP（prod-grok-backend.json）
- Qwen 官方导出 JSON（chat.qwen.ai）
- YourAIScroll / ChatWeave Exporter 导出的 JSON
- Markdown 粘贴导入

## 快速开始

1. 浏览器打开 `index.html`
2. 左侧选择来源后上传导出文件
3. 在对话工作台中勾选要迁移的对话，可逐条编辑
4. 上传 RikkaHub 备份 ZIP，点击合并，下载合并后的备份
5. 在 RikkaHub App 中导入合并后的备份

## 版本管理

```bash
# 查看当前版本
node sync_version.js

# 更新版本号并同步所有目标
node sync_version.js 1.8.0
```

同步目标：`index.html`、`edge_exporter_lite/manifest.json`、`edge_exporter_lite/popup.js`

## 浏览器扩展

`edge_exporter_lite/` 目录是 Chrome/Edge 扩展源码。在支持平台（DeepSeek、ChatGPT 等）的聊天详情页打开扩展弹窗，即可提取当前对话。

打包发布：
1. 修改扩展文件后运行 `sync_version.js` 同步版本号
2. 将 `edge_exporter_lite/` 目录打包为 ZIP

## 隐私

所有数据处理在浏览器本地完成，不经过服务器。合并前请保留原始导出文件和 RikkaHub 备份，确认无误后再删除。

## 链接

- GitHub: https://github.com/spiritherb02/ChatWeave
- RikkaHub: https://rikka-ai.com
