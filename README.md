<div align="center">

# TinyAPI

**面向开发者的 API 在线调试平台 · 353 个 RESTful 接口**

[![Website](https://img.shields.io/badge/%E7%BD%91%E7%AB%99-api.tinyaii.cn-blue?style=flat-square)](https://api.tinyaii.cn)
[![APIs](https://img.shields.io/badge/APIs-353-green?style=flat-square)](https://api.tinyaii.cn/docs)
[![License](https://img.shields.io/badge/license-MIT-yellow?style=flat-square)](LICENSE)
[![Rust](https://img.shields.io/badge/Built%20with-Rust-orange?style=flat-square)](https://www.rust-lang.org/)

RESTful 标准 · JSON 统一返回 · GET / POST 双方式 · 浏览器直接调试

[快速开始](#快速开始) · [热门接口](#热门接口) · [接口分类](#接口分类) · [文档](https://api.tinyaii.cn/docs)

</div>

---

## 什么是 TinyAPI

TinyAPI 把分散在各处的数据能力整理成统一的调用方式：同一个域名、同一套鉴权、同一种返回格式。

做应用时经常需要一些零散的数据能力——查一个城市的天气、解析一条短视频链接、取一次热榜。这些能力原本分散在不同的服务商手里，每接一家就要注册一次账号、读一遍文档、处理一套不同的错误码。TinyAPI 把这些整理成 353 个接口，开发者只需申请一个 API Key，就能按路径调用。

**适合谁**：需要快速接入数据能力的个人开发者、学生项目、独立站长。

---

## 快速开始

### 1. 获取 API Key

在 [用户中心](https://api.tinyaii.cn/user) 注册，账号信息中会自动生成 API Key。

### 2. 发起请求

API Key 通过请求头传递：

```bash
curl "https://api.tinyaii.cn/v1/quote" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

也可以放在 URL 参数里：

```bash
curl "https://api.tinyaii.cn/v1/quote?apikey=YOUR_API_KEY"
```

所有接口同时支持 GET 和 POST。

### 3. 返回格式

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

**注意**：业务状态码在响应体的 `code` 字段，**HTTP 状态恒为 200**。判断调用是否成功请读 `code`，不要看 HTTP 状态码。数据在 `data`，错误原因在 `message`。

---

## 热门接口

### 天气查询

```bash
curl "https://api.tinyaii.cn/v1/weather?city=北京&apikey=YOUR_KEY"
```

```json
{
  "code": 200,
  "data": {
    "city": "北京",
    "temp": "18",
    "weather": "晴",
    "forecast": [ ... ]
  }
}
```

### 短视频聚合解析

支持抖音、TikTok、YouTube、哔哩哔哩等平台，返回无水印地址、封面与作者信息。

```bash
curl "https://api.tinyaii.cn/v1/video/parse2?url=https://vt.tiktok.com/ZSxQ2JsN6/&apikey=YOUR_KEY"
```

### 聚合热榜

聚合知乎、微博、哔哩哔哩、GitHub 等平台的实时热榜。

```bash
curl "https://api.tinyaii.cn/v1/hot?apikey=YOUR_KEY"
```

### IP 归属地

```bash
curl "https://api.tinyaii.cn/v1/ip?ip=8.8.8.8&apikey=YOUR_KEY"
```

### 二维码生成

```bash
curl "https://api.tinyaii.cn/v1/qrcode?text=https://example.com&apikey=YOUR_KEY"
```

---

## 接口分类

| 分类 | 数量 | 示例 |
|------|------|------|
| 🎮 游戏数据 | 131 | 原神/星铁/绝区零兑换码、Steam 价格与在线人数、三角洲行动图鉴 |
| 🛠️ 实用工具 | 74 | 二维码、DNS 查询、WHOIS、MD5/SHA256、JSON 格式化、快递查询 |
| 🖼️ 图片壁纸 | 51 | 多主题随机壁纸、二次元插画 |
| 📺 内容解析 | 43 | 短视频解析、B 站视频信息、网易云音乐、各平台热榜 |
| 🎲 趣味文本 | 26 | 随机一言、毒鸡汤、绕口令、歇后语 |
| 🤖 AI 能力 | 20 | AI 对话（兼容 OpenAI 格式）、AI 识图、AI 绘画、OCR、向量化 |
| 🌤️ 生活查询 | 8 | 天气、油价、世界时间、手机号归属地 |

> 每个接口都有独立的参数说明页：`https://api.tinyaii.cn/apis/{接口名}`
>
> 完整列表见 [开发文档](https://api.tinyaii.cn/docs)

---

## 技术栈

- **后端**：Rust（Axum）+ PostgreSQL
- **前端**：原生 HTML / CSS / JS，无框架
- **部署**：Nginx 反向代理 + Let's Encrypt HTTPS
- **鉴权**：API Key（请求头或 URL 参数）

---

## 使用说明

- 接口以免费为主，注册后获得每日基础调用额度
- 部分高频或高成本接口有单独的额度限制，具体见各接口文档
- 所有接口为标准 HTTP，任何语言都能调用（JavaScript / Python / Go / PHP / C# 等）
- 数据部分来自第三方上游，商业使用请自行确认各数据源的授权条款

---

## 文档

- [开发文档](https://api.tinyaii.cn/docs) — 353 个接口的参数与返回说明
- [帮助中心](https://api.tinyaii.cn/docs/help) — 调用方式与错误码
- [完整接口索引](https://api.tinyaii.cn/docs#all-apis)

---

## License

MIT License

---

<div align="center">

**[api.tinyaii.cn](https://api.tinyaii.cn)**

</div>
