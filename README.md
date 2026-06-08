# Glance 个人仪表板配置

基于 [Glance](https://github.com/glanceapp/glance) 的自托管仪表板配置，聚合了个人基础设施、媒体服务、开发工具等状态监控。

## 包含的小部件

- **首页** — 时钟、天气、时间进度条、书签、Steam/Duolingo/Epic/Last.fm 状态
- **媒体** — Jellyfin/Immich/qBittorrent 统计、Komga 漫画/轻小说书架
- **基础设施** — Tailscale/Netbird 设备、TrueNAS/Proxmox 状态、AdGuard DNS、Syncthing 同步
- **AI** — 自托管 AI 服务监控、LLM 工具书签、APOD 天文图片
- **开发** — LeetCode 每日题目、GitHub Trending、Cloudflare Tunnel 状态、Git/注册表监控

## 前置条件

- Docker 和 Docker Compose
- 已运行的各后端服务（Jellyfin、Immich、AdGuard 等，按需启用）

## 快速开始

1. 克隆仓库
   ```bash
   git clone https://github.com/chius-me/glance-config.git
   cd glance-config
   ```

2. 配置环境变量
   ```bash
   cp .env.example .env
   # 编辑 .env，填入你的服务地址和 API 密钥
   ```

3. 创建资源目录
   ```bash
   mkdir -p assets
   ```

4. 启动
   ```bash
   docker compose up -d
   ```

5. 访问 `http://localhost:8081`

## 自定义

所有配置文件位于 `config/` 目录：

| 文件 | 页面 |
|------|------|
| `glance.yml` | 全局设置（认证、主题、页面列表） |
| `home.yml` | 首页（时钟、书签、Steam、Duolingo 等） |
| `media.yml` | 媒体页（Jellyfin、Komga、qBittorrent 等） |
| `infra.yml` | 基础设施页（Tailscale、Proxmox、TrueNAS 等） |
| `ai.yml` | AI 页（Open WebUI、ComfyUI 等自托管服务） |
| `dev.yml` | 开发页（LeetCode、Cloudflare、Git 服务等） |

## 安全

- `.env` **不应**提交到版本控制（已在 `.gitignore` 中排除）
- 所有 API 密钥通过环境变量注入，不在配置文件中硬编码
- `caddy/Caddyfile` 中的密钥请替换为自己的值
