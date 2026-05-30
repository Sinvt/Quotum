# Quotum · 每日双语名言 & 经济学知识

> A zero-dependency web app that delivers a daily bilingual (Chinese + English) quote and a piece of economics knowledge.

> 每天为你推送一条双语（中英）名言与一则经济学知识的纯前端网页应用。

**在线访问 | Live demo:** https://sinvt.github.io/Quotum/

---

## 💡 它适合谁 | Use Cases

- **想培养每日习惯的人** — 每天打开看一条，像撕日历一样为一天定个基调。
  *A daily ritual — one card each morning to set the tone for your day.*
- **跨领域的终身学习者** — 经济学模式可当作「知识闪卡」，每天一个核心概念（机会成本、看不见的手、复利……），看到不熟的点开简介，配合收藏夹复习。
  *A flashcard for lifelong learners — pick up one economics concept a day and review favorites over time.*
- **需要双语素材的人** — 写作、做幻灯片、社交媒体配文时，用搜索快速找到合适的中英双语句子。
  *A quick source of bilingual material for writing, slides, and posts.*
- **需要一点鼓励的时刻** — 随机抽一条，也许正好戳中；收藏夹是你专属的打气合集。
  *A small pick-me-up — pull a random card when you need one.*

---

## ✨ 功能 | Features

| 功能 | Feature | 说明 |
|---|---|---|
| 💬 名言模式 | Quotes | 每日推送一条中外名人双语名言 |
| 📈 经济学模式 | Economics | 每日推送一则经济学概念或格言，附背景简介 |
| 📅 每日推送 | Daily Pick | 基于日期的确定性算法，每天固定一条 |
| ➕ 再来一条 | Show More | 手动浏览库中更多条目 |
| 🎲 随机获取 | Random Fetch | 并发请求多个公开 API，取最快返回，自动翻译为中文 |
| 🔍 搜索 | Search | 按中英文 / 作者 / 简介在库中即时检索 |
| ❤️ 收藏夹 | Favorites | 收藏喜欢的条目，两个模式各自独立 |
| 🗂 历史记录 | History | 自动记录每日内容，可随时回看 |
| ✏️ 手动添加 | Add Custom | 添加你自己的名言或知识条目 |
| 🗑 删除 | Delete | 卡片、历史、收藏均可删除 |
| 🌙 日夜模式 | Dark / Light | 一键切换主题，偏好自动保存 |
| 📱 响应式 | Responsive | 手机 / 平板 / 桌面自适应 |
| 🌐 智能回退 | Smart Fallback | 联网失败时自动从本地库选取，内容不中断 |

---

## 🚀 使用方式 | Getting Started

**在线访问** — 直接打开浏览器：

```
https://sinvt.github.io/Quotum/
```

**本地运行** — 克隆后双击 `index.html` 即可，无需任何构建步骤：

```bash
git clone https://github.com/Sinvt/Quotum.git
cd Quotum
# 双击 index.html / open index.html
```

---

## 🛠 技术栈 | Tech Stack

| 层 | Technology |
|---|---|
| 前端 | Vanilla HTML / CSS / JavaScript（零依赖，无框架、无构建工具） |
| 存储 | 浏览器 localStorage（收藏、历史、主题偏好均存于本地） |
| 在线源 | ZenQuotes / PoetryDB / Wikipedia（多源并发，最快优先） |
| 翻译 | MyMemory Translation API |
| 部署 | GitHub Pages |

---

## 🎯 设计理念 | Design Principles

- **零依赖** — 不需要 npm、框架或后端，一个 HTML 文件即是全部应用。
- **离线优先** — 内置精选内容库，无网络也能正常使用。
- **多源并发** — 联网时同时请求多个公开 API，最快返回者优先。
- **隐私至上** — 所有数据仅保存在你的浏览器本地，不上传、不追踪。

> Zero dependencies · Offline-first · Multi-source concurrency · Privacy by default.

---

## 📂 项目结构 | Project Structure

```
Quotum/
├── index.html    单文件应用（含全部 HTML / CSS / JS）
└── README.md
```

---

## 📄 License

MIT
