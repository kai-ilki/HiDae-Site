# CLAUDE.md — hidae-site

這份是交接說明。回覆 Kai 時請用繁體中文書面語（不要用粵語口語）。

## 這個 repo 是什麼
- HiDae（內部代號 InnerLight）的官網 landing page。HiDae 是一個心理投射卡 app：抽圖卡 → 翻字卡 → 用引導問題自我反思。強調「不是占卜」。
- 單一檔案 `index.html`（純 HTML/CSS，沒有 build step），英文，目標用戶是歐美。
- 以 GitHub Pages 從 `main` 分支根目錄發佈：https://kai-ilki.github.io/hidae-site/
- App 本體在另一個 repo，網站刻意獨立放在這裡。

## Commit 規則
- 作者一律用：`kai-ilki <53655584+kai-ilki@users.noreply.github.com>`
- 不要用 `kai@users.noreply.github.com`，那是別人的帳號（曾經因此掛錯 contributor）。

## 網站待辦
- [ ] 填入 App Store / Google Play 下載連結（在 `index.html` 搜尋 `TODO`）
- [ ] 填入聯絡 email 和各社群帳號連結（footer）
- [x] Privacy Policy / Support 連結已填（Kai 現有的 Notion 頁面）
- [ ] 之後可考慮換成真的 app 截圖（向 Kai 索取）
- [ ] 自訂網域（選用，約 US$10–20/年）

## 下一個任務：社群帳號設定 + 自動發文
Kai 已經有 IG、Threads、TikTok、X 帳號，想要：
1. 幫她把各平台的 profile（名稱、bio、連結、大頭貼）設定好
2. 建立「AI 產生草稿 → Kai 審核 → 排程發佈」的自動發文流程

### 已擬好的 bio（可直接用）
- IG：`Stop waiting for fate. Reclaim your life. 🃏 / Draw a card, see what's hidden inside you. / ⬇️ Try HiDae free`
- TikTok：`Cards that mirror you, not your future. 🃏 Try HiDae free ⬇️`
- X：`The cards don't tell the future. They mirror what's hidden inside you. HiDae — a reflection card app for reconnecting with yourself.`
- Threads 與 IG 共用帳號。所有平台的連結都指向官網。

### Profile 設定的做法
- 平台不開放用 API 改 bio，需要用瀏覽器操作：在 Kai 的電腦開 Chrome + Claude in Chrome 擴充功能，由 Claude 代填，Kai 處理登入和驗證碼。

### 自動發文的建議架構（已討論過，Kai 傾向這個方向）
- 工具：**Postiz**（開源，AGPL-3.0，github.com/gitroomhq/postiz-app），可 self-host，支援 MCP / API / n8n，能讓 AI agent 排程發文。
- 不想付 server 費：用 Docker 跑在 Kai 自己的電腦上（細節問 Kai）。
- 各平台發文權限（需要逐一確認目前規定）：
  - IG / Threads：要轉成 Business 或 Creator 帳號，並建立 Meta developer app 取得發文權限 —— 通常是最花時間的一步
  - TikTok：Content Posting API 需要申請 / 審核
  - X：確認目前 API 方案是否允許免費發文
- 一定要保留人工審核：HiDae 是心理反思類內容，AI 草稿不能聽起來像心理診斷或占卜預言。
- 內容方向還沒定案：先做 profile 和基礎設定，內容主軸等用戶回饋後再定。
