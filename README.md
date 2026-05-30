# Quotum · 每日双语名言 & 经济学知识

> 📖 A daily dose of bilingual wisdom — quotes and economics knowledge, online and offline.

> 📖 每日一句双语名言 + 经济学知识，支持联网搜索与离线浏览。

---

## ✨ 功能 | Features

| 功能 | Feature | 说明 |
|---|---|---|
| 💬 名言模式 | Quotes Mode | 每日推送一条双语名言（50 条精选库） |
| 📈 经济学模式 | Economics Mode | 每日推送一条经济学知识（45 条精选库） |
| 🎲 随机获取 | Random Fetch | 同时向 ZenQuotes / PoetryDB / Wikipedia 三个 API 并发请求，取最快返回结果，中英双语 |
| 🔍 本地搜索 | Local Search | 在全部条目中按中英文 / 作者 / 简介即时搜索 |
| ❤️ 收藏夹 | Favorites | 收藏喜欢的条目，两个模式各自独立存储 |
| 📅 历史记录 | History | 每日名言/知识自动记录，支持翻看过往 |
| ✏️ 手动添加 | Add Custom | 自定义名言或知识条目 |
| 🌙 夜间/日间模式 | Dark/Light Mode | 一键切换，偏好自动保存 |
| 📱 响应式设计 | Responsive | 手机 / 平板 / 桌面均可使用 |
| 🌐 智能回退 | Smart Fallback | 联网失败时自动从本地库选取，保证内容不中断 |

---

## 🚀 如何使用 | How to Use

### 在线访问 | Online

直接打开浏览器访问：

```
https://sinvt.github.io/Quotum/
```

### 本地使用 | Local

```bash
git clone https://github.com/Sinvt/Quotum.git
cd Quotum
# 双击 index.html 即可
# Or double-click index.html
```

---

## 🛠 技术栈 | Tech Stack

| 层 | 技术 | Technology |
|---|---|---|
| 前端框架 | 纯 HTML/CSS/JS (零依赖) | Vanilla HTML/CSS/JS (zero dependencies) |
| 数据存储 | 浏览器 localStorage | Browser localStorage |
| 名言数据源 | 内置精选库 (95 条) | Built-in curated library (95 items) |
| 在线 API | ZenQuotes / PoetryDB / Wikipedia | ZenQuotes / PoetryDB / Wikipedia |
| 翻译引擎 | MyMemory Translation API | MyMemory Translation API |
| 部署 | GitHub Pages | GitHub Pages |

---

## 📂 项目结构 | Project Structure

```
Quotum/
├── index.html    ← 全部代码（单文件应用）| Single-file application
└── README.md     ← 本文件 | This file
```

---

## 🎯 设计理念 | Design Philosophy

- **零依赖** — 不需要 npm、不需要构建工具、不需要后端服务器
- **离线优先** — 本地 95 条精选内容确保无网络也能使用
- **多源并发** — 联网时从多个 API 同时获取，最快响应优先
- **隐私第一** — 所有数据保存在用户浏览器本地，不上传任何信息

> Zero dependencies, offline-first, multi-source concurrency, privacy-first.

---

## 📄 许可 | License

MIT

---

*Made with ❤️ by Sinvt · Powered by vanilla HTML/CSS/JS*
