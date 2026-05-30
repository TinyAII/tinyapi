<div align="center">

# TinyAPI

**免费 · 开源 · 146+ 个 API 接口**

[![Website](https://img.shields.io/badge/网站-api.tinyaii.top-blue?style=flat-square)](https://api.tinyaii.top)
[![APIs](https://img.shields.io/badge/APIs-146+-green?style=flat-square)](https://api.tinyaii.top/apis)
[![License](https://img.shields.io/badge/license-MIT-yellow?style=flat-square)](LICENSE)
[![Rust](https://img.shields.io/badge/Built%20with-Rust-orange?style=flat-square)](https://www.rust-lang.org/)

RESTful 标准 · JSON 格式 · GET/POST 双方式 · 注册即用 · 无需付费

[快速开始](#快速开始) · [API 分类](#api-分类) · [文档](https://api.tinyaii.top/docs) · [在线调试](https://api.tinyaii.top/apis)

</div>

---

## 什么是 TinyAPI？

TinyAPI 是一个免费的 API 接口聚合平台，提供 146+ 个开箱即用的 API，覆盖短视频解析、AI 搜索、天气查询、IP 定位、二维码生成、翻译、加密解密等 18 个分类。

**适合谁？** 个人开发者、学生项目、初创团队、独立站长——任何需要快速接入 API 的人。

---

## 快速开始

### 1. 注册获取 API Key

访问 [api.tinyaii.top/user](https://api.tinyaii.top/user) 注册账号，获取免费 API Key。

### 2. 发起请求

**GET 方式：**
```bash
curl "https://api.tinyaii.top/v1/quote" \
  -H "Authorization: Bearer sk_your_api_key"
```

**POST 方式（所有 API 同时支持）：**
```bash
curl -X POST "https://api.tinyaii.top/v1/quote" \
  -H "Authorization: Bearer sk_your_api_key" \
  -H "Content-Type: application/json" \
  -d '{}'
```

**返回格式：**
```json
{
  "code": 200,
  "message": "success",
  "data": {
    "content": "业精于勤荒于嬉，行成于思毁于随。",
    "source": "韩愈"
  }
}
```

---

## 热门接口示例

### 🎬 聚合短视频解析

支持 1000+ 平台（TikTok、YouTube、B站、Twitter、Pinterest 等）。

```bash
curl "https://api.tinyaii.top/v1/video/parse2?url=https://vt.tiktok.com/ZSxQ2JsN6/" \
  -H "Authorization: Bearer sk_your_api_key"
```

```json
{
  "code": 200,
  "data": {
    "title": "视频标题",
    "platform": "tiktok",
    "items": [
      {"type": "video", "url": "https://..."},
      {"type": "image", "url": "https://..."}
    ]
  }
}
```

### 🔍 智能搜索

AI 驱动的网页搜索，支持智能问答。

```bash
curl "https://api.tinyaii.top/v1/web/search?query=今天天气" \
  -H "Authorization: Bearer sk_your_api_key"
```

```json
{
  "code": 200,
  "data": {
    "query": "今天天气",
    "answer": "今天全国大部分地区晴好，气温适宜。",
    "results": [
      {"title": "天气预报", "url": "https://...", "content": "...", "score": 0.95}
    ]
  }
}
```

### 🎤 语音转文字

支持 MP3/WAV/M4A/OGG/FLAC，最大 25MB。

```bash
curl "https://api.tinyaii.top/v1/audio/asr?url=https://example.com/audio.mp3" \
  -H "Authorization: Bearer sk_your_api_key"
```

```json
{
  "code": 200,
  "data": {
    "text": "识别出的文字内容"
  }
}
```

---

## API 分类

| 分类 | 数量 | 示例接口 |
|------|------|----------|
| 🎮 游戏 | 20 | 原神随机图片、明日方舟干员查询、王者荣耀战力 |
| 🎲 趣味 | 14 | 毒鸡汤、彩虹屁、春联生成、歇后语 |
| 🎨 随机图片 | 14 | 原神/崩坏/明日方舟/海贼王等壁纸 |
| 🚗 生活 | 12 | 油价查询、农历、星座运势、历史上的今天 |
| 🤖 AI | 12 | 智能搜索、语音转文字、动漫搜番、AI对话 |
| 📝 文本 | 11 | 文本统计、拼音转换、MD5/SHA256、JSON格式化 |
| 🛠️ 开发 | 10 | 二维码生成、DNS查询、Favicon获取、IP查询 |
| 🔥 热榜 | 9 | 聚合热榜、微博热搜、B站热门、GitHub趋势 |
| 🔒 加密 | 9 | AES/RSA/DES加密解密、Base64编解码 |
| 🌐 网络 | 6 | IP归属地、天气查询、WHOIS查询 |
| 💬 社交 | 5 | B站视频信息、微博用户信息 |
| 🎬 视频 | 3 | 聚合短视频解析（1000+平台）|
| 🎵 音乐 | 4 | 网易云音乐解析/搜索/排行榜 |
| 📦 其他 | 8 | 快递查询、油价、短链接生成 |

> 完整接口列表：[api.tinyaii.top/apis](https://api.tinyaii.top/apis)

---

## 技术栈

- **后端**: Rust (Axum) + PostgreSQL
- **前端**: 纯 HTML/CSS/JS SPA
- **移动端**: Flutter (相册项目)
- **部署**: Nginx + Let's Encrypt HTTPS
- **服务器**: 香港云服务器

---

## 文档

- [开发者文档](https://api.tinyaii.top/docs)
- [帮助中心](https://api.tinyaii.top/docs/help)
- [API 分类列表](https://api.tinyaii.top/apis)

---

## License

MIT License

---

<div align="center">

**[api.tinyaii.top](https://api.tinyaii.top)** · 免费 · 无限制 · 注册即用

</div>
