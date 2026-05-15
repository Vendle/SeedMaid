# SeedMaid 🌱

[![Docker Image](https://img.shields.io/badge/docker-vendle%2Fseedmaid-blue?logo=docker)](https://hub.docker.com/r/vendle/seedmaid)
[![Version](https://img.shields.io/badge/version-2.0.0-blue)]()
[![Platform](https://img.shields.io/badge/platform-linux%2Famd64%2Farm64-blue)]()

## 💎 购买授权

> **对于合理且必要的用户需求，会在能力范围内尽快响应并落实，最终实现自动化媒体库一站式服务。**

> **支持7天免费试用，觉得好用再来支持。**

### 授权价格

| 授权类型 | 价格 | 说明 |
|---------|------|------|
| 永久授权 | ¥95 | 一次性购买，永久使用，支持 1 个设备 |
| 永久授权 | 早鸟价¥66 | 一次性购买，永久使用，支持 1 个设备 |

> 💡 注：95元非固定售价，随着功能的增加，价格也会随时变化。

### 购买流程

1. **扫描下方二维码支付**
2. **付款时备注您的邮箱地址**（用于接收授权码）
3. 作者确认后会将授权码发送至您提供的邮箱
4. 在 SeedMaid 登录页的「激活授权」中输入授权码即可

> 💡 提示：若邮箱过长备注不全，可在付款后通过下方联系方式告知。

### 支付方式

<details>
<summary>点击展开微信收款码</summary>

<!-- 请将收款码图片替换为实际图片，例如：docs/assets/wechat-pay.png -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Vendle/SeedMaid/main/docs/assets/wechat-pay-placeholder.png" alt="微信支
  付" width="240">
  <br>
  <sub>微信扫码支付</sub>
</p>

</details>

<details>
<summary>点击展开支付宝收款码</summary>

<!-- 请将收款码图片替换为实际图片，例如：docs/assets/alipay.png -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Vendle/SeedMaid/main/docs/assets/alipay-placeholder.png" alt="支付宝" wi
  dth="240">
  <br>
  <sub>支付宝扫码支付</sub>
</p>

</details>

### 重要提示

- ⚠️ 授权码仅限支持同时在线 **1 个设备**，超出数量会导致授权被封禁
- 📧 请务必在付款时备注您的邮箱，否则无法发送授权码
- 🔄 更换设备时可先在原设备「关于」页面中「解绑授权」，再在新设备激活

### 联系方式

如有任何问题，欢迎联系：

- **Telegram**: [@Vendle_Liu](https://t.me/Vendle_Liu)
- **Telegram频道**：[@SeedMaid](https://t.me/SeedMaid)
- **Email**: vendle.liu@qq.com
    
---

## 💬 支持

- Docker Hub: [vendle/seedmaid](https://hub.docker.com/r/vendle/seedmaid)

---

## 🚀 快速开始

### 环境要求
- Docker 20.10+ 或 Docker Desktop
- 支持平台：`linux/amd64`、`linux/arm64`

### Docker Compose（推荐）

```yaml
services:
  seedmaid:
    image: vendle/seedmaid:latest
    container_name: seedmaid
    restart: unless-stopped
    ports:
      - "666:666"
    environment:
      - TZ=Asia/Shanghai
      - SEEDMAID_USERNAME=admin
      - SEEDMAID_PASSWORD=seedmaid
    volumes:
      - ./seeds:/app/seeds
      - ./config:/app/data
      - /media:/downloads
      - /var/run/docker.sock:/var/run/docker.sock:ro
```

```bash
docker compose up -d
```

### Docker Run

```bash
docker run -d \
  --name seedmaid \
  -p 666:666 \
  -e TZ=Asia/Shanghai \
  -e SEEDMAID_USERNAME=admin \
  -e SEEDMAID_PASSWORD=seedmaid \
  -v $(pwd)/seeds:/app/seeds \
  -v $(pwd)/config:/app/data \
  -v /media:/downloads \
  -v /var/run/docker.sock:/var/run/docker.sock:ro \
  --restart unless-stopped \
  vendle/seedmaid:latest
```

### 登录系统

容器启动后，访问 `http://<服务器IP>:666`，使用 Docker 环境变量中设置的账号密码登录。

默认账号：`admin` / `seedmaid`

---

## ⚙️ 配置指南

### 环境变量

| 变量 | 默认值 | 说明 |
|------|--------|------|
| `SEEDMAID_USERNAME` | `admin` | Web 登录用户名 |
| `SEEDMAID_PASSWORD` | `seedmaid` | Web 登录密码 |
| `TZ` | `Asia/Shanghai` | 容器时区 |

### 数据持久化

| 宿主机路径 | 容器路径 | 说明 |
|------------|----------|------|
| `./config` | `/app/data` | 配置文件、数据库、缓存|
| `./seeds` | `/app/seeds` | 种子下载目录 |
| `/media` | `/downloads` | 下载器联动目录 |
| `/var/run/docker.sock` | `/var/run/docker.sock` | Docker Socket（自更新用） |

> ⚠️ **重要**：务必挂载 `/app/data` 卷，否则容器重建后所有数据将丢失！

---


<p align="center">
  <sub>🌱 SeedMaid — 自动化媒体库管理</sub>
</p>
