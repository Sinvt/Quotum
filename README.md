# Quotum · 每日双语名言 & 古诗 & 经济学知识

> A zero-dependency web app delivering daily bilingual wisdom — quotes, classical Chinese poetry, and economics.

> 每天为你推送双语（中英）名言、中国古典诗词与经济学知识的前端网页应用，现已支持接入本地大语言模型（LLM）进行智能知识创作。

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
- **品味中国古典诗词的人** — 每天一首李白、杜甫、苏轼……中英双语对照，在工科日常里留一扇看往千年之前的窗。
  *A window into classical Chinese poetry — one poem a day with English translation.*

---

## ✨ 功能 | Features

| 功能 | Feature | 说明 |
|---|---|---|
| 💬 名言模式 | Quotes | 每日推送一条中外名人双语名言 |
| 🏔 古诗模式 | Poetry | 每日推送一首中国古典诗词（李白/杜甫/苏轼……），中英双语 |
| 📈 经济学模式 | Economics | 每日推送一则经济学概念或格言，附背景简介 |
| 📅 每日推送 | Daily Pick | 基于日期的确定性算法，每天固定一条 |
| ➕ 再来一条 | Show More | 手动浏览库中更多条目 |
| 🎲 随机获取 | Random Fetch | 优先调用本地 LLM 智能生成，后端未启动时平滑降级至互联网 API（jinrishici / ZenQuotes 等） |
| 🔍 智能搜索 | AI Search | 支持调用 LLM 根据你的关键词即席创作知识卡片，失败则自动回退本地库搜索 |
| ❤️ 收藏夹 | Favorites | 收藏喜欢的条目，三个模式各自独立 |
| 🗂 历史记录 | History | 自动记录每日内容，可随时回看 |
| ✏️ 手动添加 | Add Custom | 添加你自己的名言、诗词或知识条目 |
| 🗑 删除 | Delete | 卡片、历史、收藏均可删除 |
| 🌙 日夜模式 | Dark / Light | 一键切换主题，偏好自动保存 |
| 📱 响应式 | Responsive | 手机 / 平板 / 桌面自适应 |
| 🌐 智能回退 | Smart Fallback | 联网失败时自动从本地精选库选取，内容不中断 |

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

## 🧠 本地大模型部署指南 | Local LLM Setup

本项目内置了联动本地大语言模型（LLM）的智能增强功能。按照以下步骤即可启用：

1. **模型下载 (Model Download)**：
   推荐前往 Hugging Face 或 ModelScope 下载 **Qwen3-8B-Instruct** 的 GGUF 格式量化文件（例如 `qwen3-8b-instruct-q4_k_m.gguf`）。下载完成后，请直接将该模型文件放入项目的根目录中。
2. **后端编译与启动 (Backend Compilation & Launch)**：
   本项目与 `llama.cpp` 配合运行。请克隆 `llama.cpp` 官方仓库并开启 CUDA 编译（例如 `make GGML_CUDA=1`）。或者直接下载官方预编译版本，双击项目自带的 `start_api.bat` 一键启动服务端。
3. **端口配置 (Port Settings)**：
   本地 LLM 后端默认将在 `127.0.0.1:8080` 暴露兼容 OpenAI 规范的 API 接口，前端会自动连接该地址获取内容。

---

## 🏗 架构简析 | Architecture Notes

本项目在实现 AI 接入时，注重轻量化与稳定性，主要包含以下基础设计：

- **硬件友好的本地部署 (Local Deployment)**：
  针对家用显卡（如 8GB 显存），推荐使用 GGUF 格式配合 `llama.cpp`，在较低显存占用下实现大模型的 GPU 加速推理。

- **轻量级提示词与结构化输出 (Lightweight Prompting)**：
  没有引入复杂的 Agent 框架，仅依靠原生 JavaScript 发起请求。通过 System Prompt 设定角色，要求模型直接返回严格的 JSON 格式数据以便于卡片渲染。

- **平滑降级机制 (Graceful Fallback)**：
  前端在请求本地 LLM 失败（例如服务未开启或请求超时）时，会自动拦截异常并无缝回退至原有的公网 API 或本地静态数据库，保证应用始终可用。

---

## 🛠 技术栈 | Tech Stack

| 层 | Technology |
|---|---|
| 前端 | Vanilla HTML / CSS / JavaScript（零依赖，无构建工具） |
| 大模型支持 | 接入 `llama.cpp` 本地服务端（支持 Qwen3 等模型）进行实时推理 |
| 存储 | 浏览器 localStorage（收藏、历史、主题偏好均存于本地） |
| 在线源 | jinrishici.com / ZenQuotes / PoetryDB 等公网 API |
| 翻译 | MyMemory Translation API |
| 部署 | GitHub Pages |

---

## 🎯 设计理念 | Design Principles

- **AI 加持，高可用兜底** — 优先调度本地大语言模型创作无尽内容，若未启动则无缝回退至静态库与公网 API。
- **零依赖与离线优先** — 不需要 npm、框架或后端（除可选的 LLM 服务外），一个 HTML 文件即是全部核心应用。
- **隐私至上** — 所有数据仅保存在你的浏览器本地，AI 推理在本地显卡完成，不上传、不追踪。

> Local LLM Ready · High-Availability Fallback · Offline-first · Privacy by default.

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

---

*Made with ❤️ by Sinvt · Powered by vanilla HTML/CSS/JS*
