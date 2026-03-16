# Skills 使用经验

## 概览

OpenClaw 提供了丰富的 skills（技能），分为本地 skills 和全局 skills。

### 本地 Skills（workspace/skills/）

| Skill | 用途 |
|-------|------|
| github | GitHub API 操作 |
| discord / discord-chat | Discord 消息发送和管理 |
| tts / bailian-tts / tts-whatsapp | 文字转语音 |
| weather | 天气预报 |
| summarize | 摘要 URL/文件 |
| polymarket | 预测市场 |
| feishu-edge-tts-win | 飞书语音消息（Windows） |
| feishu-docs | 飞书文档操作 |
| tencent-cos-skill | 腾讯云对象存储 |
| tencentcloud-lighthouse | 腾讯云轻量应用服务器 |
| tencentcloud-tts | 腾讯云语音合成 |
| playwright-browser | 浏览器自动化 |
| agent-browser | Rust 浏览器自动化 |
| obsidian | Obsidian 笔记操作 |
| scraping-recipes | 网页抓取模板 |
| tavily-search | AI 优化搜索 |
| find-skills | 查找安装新 skills |
| clawhub | ClawHub skills 管理 |
| topclawhubskills / trending-skills | 热门 skills 排行 |
| self-improving-agent | 自我改进经验记录 |

---

## GitHub 操作经验

### 使用 GitHub API

```bash
# 创建仓库
curl -X POST https://api.github.com/user/repos \
  -H "Authorization: token $TOKEN" \
  -d '{"name":"repo-name","private":false}'

# 查看仓库列表
curl -H "Authorization: token $TOKEN" \
  "https://api.github.com/user/repos?per_page=100"
```

### 注意事项

1. **Fine-grained PAT 权限**：需要配置 Administration (Read and write) 和 Contents (Read and write) 权限
2. **Classic PAT**：直接勾选 repo 权限即可
3. **SSH vs HTTPS**：推荐使用 SSH，避免认证问题

---

## Discord 操作经验

### 发送消息

```javascript
// 使用 message 工具
message action=send channel=discord target="channel-id" message="内容"
```

### 常用操作

- `send` - 发送消息
- `react` - 添加反应
- `search` - 搜索消息
- `thread-create` - 创建线程
- `channel-list` - 列出频道

---

## 浏览器自动化经验

### Playwright Browser

- 需要 GUI 环境（本地运行）
- VPS 无 GUI 时无法使用
- 可用 headless 模式但功能受限

### Agent Browser

- Rust 实现的轻量浏览器
- 支持导航、点击、输入、截图

---

## 飞书操作经验

### 权限要求

- 需要飞书开放平台应用权限
- 文档需要先获取 node_id

### 常用操作

- 读取文档内容
- 创建/编辑文档
- 上传下载文件

---

## 腾讯云操作经验

### 需要配置

- SecretId / SecretKey
- 地域 region（如 ap-shanghai）

### 支持服务

- COS 对象存储
- Lighthouse 轻量服务器
- TTS 语音合成
- CI 图片处理

---

## Skills 发现与安装

### 查找 Skills

```bash
# 本地搜索
clawhub search <keywords>

# 在线热门
clawhub trending
```

### 安装 Skills

```bash
clawhub install <skill-name>
```

### 发布 Skills

```bash
clawhub publish <skill-path>
```

---

## 自我改进记录

每次遇到以下情况时应记录经验：

1. 命令或操作意外失败
2. 用户纠正你的回答
3. 用户请求不存在的功能
4. 外部 API 或工具失败
5. 发现知识过时或不正确
6. 发现更好的方法

使用 `self-improving-agent` skill 记录。

---

## 更新日志

- 2026-03-16: 初始版本，记录 GitHub、Discord、浏览器、飞书、腾讯云等经验
