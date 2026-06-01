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
   本项目底层与 `llama.cpp` 深度解耦但默契联动。请克隆 `llama.cpp` 官方仓库，并强制开启 CUDA 硬件加速进行编译（例如使用 `make GGML_CUDA=1`）。编译完成后，双击项目自带的 `start_api.bat`（Windows）或执行 `start_api.sh` 脚本以一键启动服务端。
3. **端口与跨域配置 (Port & CORS)**：
   本地 LLM 后端默认将在 `127.0.0.1:8080` 暴露完美兼容 OpenAI 规范的 API 接口。**注意**：在手动启动服务端时，必须携带 `--cors` 参数，以允许前端网页安全跨域连入并执行推理请求。

---

## 🏗 架构与技术深度 | Architecture & Technical Depth

从重度工程与现代 AI 侧端应用的角度，本项目呈现了以下底层技术亮点：

- **极致的显存控制与硬件感知 (Hardware-Aware Optimization)**：
  在严格受限的 8GB 显存（如 RTX 5070）物理红线内，系统通过死磕 4-bit/5-bit 高性能量化技术（GGUF），将模型全量卸载（Offload）到 GPU 上。在极致压榨显存空间的同时，为长文本留出充裕的 KV Cache 空间，从而在单批次推理中榨干硬件算力，实现极低的首字延迟（TTFT）与惊艳的吞吐率。这种在受限硬件环境下追求极致执行效率的逻辑，与边缘计算或卫星端低级硬件加速的调优思想完全契合。

- **轻量级单 Agent 编排与结构化对齐 (Lightweight Agent Orchestration)**：
  项目果断摒弃了臃肿的外部 Agent 编排框架，由前端纯原生 JavaScript 直接充当轻量级的 Agent 意图识别与调度节点。底层注入了极其严密的 System Prompt（角色设定），让模型扮演“内容主编”，自主进行意图路由（智能判断当前处于名言、经济学还是古诗模式），并施加强力的输出格式约束，迫使大模型在不浪费多余 Token 说废话的前提下，百分之百稳定吐出严格契合前端卡片渲染架构的纯净 JSON 数据。

- **前瞻性高可用容灾解耦 (Graceful Degradation & Fallback)**：
  系统在网络层具备工业级稳健的容灾机制。前端调度器在被触发时，会优先向本地高性能 LLM 发起推理请求（成功渲染时将被赋予专属的 `✨ AI 实时生成` 视觉标识与动态发光 UI）。一旦底层 fetch 捕获到服务未启动、连接拒绝或超时等异常，系统会在毫秒级瞬间触发平滑降级（Fallback）策略，无缝切回内置的静态精选库或传统的公网 API。这种前瞻性的绝对解耦设计，确保了应用在任何极端环境下的绝对可用性。

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
