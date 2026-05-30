# TinyAPI 开发者文档

> 免费 API 接口服务平台 · 146+ 个接口 · 注册即用

## 基础信息

| 项目 | 说明 |
|------|------|
| Base URL | `https://api.tinyaii.top` |
| 协议 | HTTPS |
| 格式 | JSON |
| 认证 | `Authorization: Bearer sk_xxx` Header |
| 额度 | 10,000 次/天（免费） |
| 请求方式 | 所有接口同时支持 GET 和 POST |

## 认证

所有 `/v1/` 开头的接口需要 API Key 认证（`/v1/friend-links`、`/v1/api-status`、`/v1/announcements` 除外）。

**方式一：Header（推荐）**
```
Authorization: Bearer sk_your_api_key
```

**方式二：Query 参数**
```
GET /v1/ip?ip=8.8.8.8&apikey=sk_your_api_key
```

## 通用返回格式

```json
{
  "code": 200,
  "message": "success",
  "data": { ... }
}
```

**错误码：**
- `400` - 参数错误
- `401` - 未认证或 API Key 无效
- `403` - API 已关闭
- `429` - 请求频率超限
- `500` - 服务器内部错误

## 接口列表

### 网络工具

#### GET /v1/ip
查询 IP 地址归属地。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| ip | string | 否 | IP 地址（不传则返回调用者IP） |

```bash
curl "https://api.tinyaii.top/v1/ip?ip=8.8.8.8" -H "Authorization: Bearer sk_xxx"
```

#### GET /v1/weather
查询城市天气。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| city | string | 是 | 城市名称 |

```bash
curl "https://api.tinyaii.top/v1/weather?city=北京" -H "Authorization: Bearer sk_xxx"
```

#### GET /v1/dns
DNS 记录查询。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| domain | string | 是 | 域名 |

```bash
curl "https://api.tinyaii.top/v1/dns?domain=baidu.com" -H "Authorization: Bearer sk_xxx"
```

### 视频解析

#### GET /v1/video/parse2
聚合短视频解析，支持 1000+ 平台（TikTok、YouTube、B站、Twitter 等）。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| url | string | 是 | 视频分享链接 |

```bash
curl "https://api.tinyaii.top/v1/video/parse2?url=https://vt.tiktok.com/ZSxQ2JsN6/" -H "Authorization: Bearer sk_xxx"
```

### AI 接口

#### GET /v1/web/search
AI 智能搜索，支持问答和网页结果聚合。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| query | string | 是 | 搜索关键词 |
| max_results | int | 否 | 最大结果数（默认5，最大10） |
| search_depth | string | 否 | basic 或 advanced |
| include_answer | bool | 否 | 是否包含AI回答（默认true） |

```bash
curl "https://api.tinyaii.top/v1/web/search?query=TinyAPI" -H "Authorization: Bearer sk_xxx"
```

#### GET /v1/audio/asr
语音转文字，支持 MP3/WAV/M4A/OGG/FLAC，最大 25MB。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| url | string | 是 | 音频文件直链 URL |

```bash
curl "https://api.tinyaii.top/v1/audio/asr?url=https://example.com/audio.mp3" -H "Authorization: Bearer sk_xxx"
```

#### GET /v1/anime/search
动漫搜番，通过截图识别动画名称、集数、时间点。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| url | string | 是 | 动漫截图 URL |

```bash
curl "https://api.tinyaii.top/v1/anime/search?url=https://example.com/anime.jpg" -H "Authorization: Bearer sk_xxx"
```

#### POST /v1/chat/completions
AI 对话（Qwen3.6-Plus）。

```bash
curl -X POST "https://api.tinyaii.top/v1/chat/completions" \
  -H "Authorization: Bearer sk_xxx" \
  -H "Content-Type: application/json" \
  -d '{"prompt": "你好"}'
```

### 工具接口

#### GET /v1/qrcode
生成二维码（返回 PNG 图片）。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| text | string | 是 | 二维码内容 |

#### GET /v1/translate
多语言翻译。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| text | string | 是 | 待翻译文本 |
| from | string | 否 | 源语言（默认自动检测） |
| to | string | 否 | 目标语言（默认英语） |

#### GET /v1/shorten
短链接生成。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| url | string | 是 | 长链接 |
| slug | string | 否 | 自定义短码 |
| expired_hours | int | 否 | 过期时间（小时） |

#### POST /v1/image/upload
图床上传，支持两种方式：
- **URL 方式**：`GET /v1/image/upload?url=https://example.com/img.jpg`
- **文件方式**：`POST /v1/image/upload`（binary body）

### 热榜/资讯

#### GET /v1/hot
聚合热榜（微博、B站、知乎、抖音等平台）。

#### GET /v1/news/60s
每日新闻（60秒读懂世界）。

#### GET /v1/bilibili/parse
B站视频解析。

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| url | string | 是 | B站视频链接 |

### 更多接口

完整接口列表请访问：[api.tinyaii.top/apis](https://api.tinyaii.top/apis)

---

## 错误处理

所有错误返回统一格式：

```json
{
  "code": 400,
  "message": "错误描述",
  "data": null
}
```

## 限流

- 每日额度：10,000 次/天
- 分钟限流：60 次/分钟（默认，部分接口 30 次/分钟）
- 限流响应码：429

## 联系方式

- 网站：[api.tinyaii.top](https://api.tinyaii.top)
- 反馈：通过网站反馈系统提交
