# 專案介紹



本專案為協作開發任務，使用 **React + Vite** 作為前端框架，並搭配 **Tailwind CSS** 進行樣式管理與 RWD 設計。
## 📚 目錄


- [開發規劃](#開發規劃)
- [專案說明](#專案說明)
- [使用技術](#使用技術)
- [開發與協作流程](#開發與協作流程)
- [專案資料結構](#專案資料結構)
- [本地運行方式](#本地運行方式)

---
## 開發規劃

- 專案採 **頁面導向拆分**（Rocket / Workspace）
- UI 元件依功能與頁面領域拆分
- 靜態資料（畫面渲染用）與元件邏輯分離
- 以 RWD 為開發前提，優先處理 mobile → desktop
- 所有功能與版型調整皆透過 PR 進行

---
## 專案說明
### 火箭隊官方網站

- 火箭隊介紹
  - 培訓相關資料
  - 師資陣容
  - 協辦 / 主辦單位資訊

### 共同空間（Co-working Space）

- 場域空間說明
- 服務項目介紹
- 進駐方案與費用展示
- 進駐表單導引（外部連結）

---
## 使用技術
### 核心技術
[![React](https://img.shields.io/badge/React-19.2-61DAFB?logo=react)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-7.2-646CFF?logo=vite)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.1-38B2AC?logo=tailwind-css)](https://tailwindcss.com/)
### 路由與互動
- React Router DOM `7.11.0`
- Swiper `12.0.3`（輪播 / Carousel）
### 工具與品質控管
- ESLint `9.39.1`
- @vitejs/plugin-react-swc `4.2.2`（使用 SWC 加速編譯）
- Type definitions：@types/react、@types/react-dom
---
## 專案資料結構
### 根目錄

- `index.html`：應用程式入口 HTML
- `vite.config.js`：Vite 設定檔
- `package.json`：npm 指令與專案相依套件設定

### 目錄結構

- `src/`
    - `main.jsx`：應用程式啟動與 Router 初始化
    - `App.jsx`：主要版型與頁面入口、路由設定
    - `assets/imgs`：圖片、Icon 等靜態資源
    - `assets/styles`：共用字型樣式、主體顏色、動畫效果
    - `components/`：共用區塊元件
    - `components/hooks`：橫向拖動捲動功能
    - `pages/`：頁面元件
```text=
ROCKET/
├─ node_modules/            # 套件相依（自動產生）
├─ src/
│  ├─ assets/               # 靜態資源
│  │  ├─ imgs/              # 圖片、Icon、輪播等影像資源
│  │  └─ styles/            # 全站樣式設定
│  │     ├─ common/         # 共用字型樣式、主體顏色、動畫效果
│  │     └─ index.css       # Tailwind CSS 入口與全域樣式
│  │
│  ├─ components/           
│  │  ├─ common/            # 共用元件
│  │  ├─ hooks/             # 自訂 Hooks（如橫向拖動捲動）
│  │  ├─ rocket/            # 火箭隊頁面相關元件
│  │  └─ workspace/         # 共同空間頁面相關元件
│  │
│  ├─ data/                 # 靜態資料（畫面渲染用）
│  │  ├─ rocket/            # 火箭隊相關資料
│  │  └─ workspace/         # 共同空間相關資料
│  │
│  ├─ pages/                # 頁面層級元件
│  │  ├─ Home.jsx           # 路由容器＋頁面切換
│  │  ├─ Rocket.jsx         # 火箭隊頁面
│  │  └─ Workspace.jsx      # 共同空間頁面
│  │
│  ├─ App.jsx               # 主要版型與路由設定
│  └─ main.jsx              # 應用程式進入點（初始化 React & Router）
│
├─ .gitignore
├─ eslint.config.js         # ESLint 設定
├─ index.html               # HTML 入口
├─ package.json             # 專案設定與套件相依
├─ package-lock.json
├─ README.md
└─ vite.config.js           # Vite 設定
```





## 開發與協作流程

本文件用於說明本專案的協作流程、Git 使用規範與開發共識。  
請所有參與成員在開始開發前閱讀並遵守。

---

## 🧑‍🤝‍🧑 協作方式

- 本專案為 **多人協作開發（3 人）**
- 所有程式碼合併皆透過 **Pull Request（PR）**
- 任務與進度以 **Notion** 進行管理與追蹤

---

## 🌿 分支命名規範

> 第一個字母需小寫，不加動詞，使用 **kebab-case**

### 命名格式
category/branch-name
### 範例
feature/homepage
update/workspace-layout
fix/header-overflow
### 分支類型

| Category | 用途 |
| --- | --- |
| feature/* | 新增功能 |
| update/* | 更新、優化既有功能 |
| fix/* | 修復 Bug |
| hotfix/* | 修復重大 Bug |
| refactor/* |改結構 / 可維護性 |
| chore/* | 專案整理及雜項設定 |

---

## 🔀 Git Flow 規範

### 🔒 main

- ❌ 禁止直接在 `main` 進行任何操作  
  （包含 commit / push / merge / force-push）
- 僅接受來自 `dev` 的 Pull Request

---

### 🔧 dev

- `dev` 由 `main` 建立
- 作為整合分支，負責：
  - 合併各功能 branch
  - 解衝突
  - 與 `main` 同步
- `dev → main` 的 PR：
  - 標題需加上 **日期或流水號**

---

### 🌱 branch（功能分支）

- 所有 branch **只能從 `dev` 建立**
- branch 僅能：
  - merge `dev`（同步或解衝突）
- ❌ 禁止 merge `main` 或其他 branch
- branch 的 PR：
  - 只能發給 `dev`
  - PR 標題需與 branch 名稱一致
- branch 與 commit：
  - 使用英文
  - 命名需統一、無錯字

---

## 📝 Commit 訊息規範

> 使用「冒號 `:`」分隔類型與描述

### 格式
type: short description
### 範例
feat: add workspace pricing cards
style: adjust typography spacing
refactor: move workspace data to data folder
### Commit 類型說明

| Type | 用途 |
| --- | --- |
| feat | 新增功能 |
| update | 更新既有功能 |
| fix / resolve | 修復 Bug |
| style | 樣式調整（字體、間距、顏色，不影響功能） |
| perf | 效能改善 |
| chore | 工具、設定、流程相關 |
| refactor | 重構（不改變功能行為） |

---

## 📦 Pull Request（PR）規範

### PR 標題

- 必須與 **分支名稱完全一致**
- 使用 kebab-case（不可有空格）

### PR 描述

- 一律使用中文
- 請以列點方式說明：
  - 修改內容
  - 影響範圍
  - 是否影響 RWD / 結構 / 資料

### 合併條件

- PR 至少需 **1 則以上 comment**
- 通過驗收後方可 merge
- 合併完成後（除 dev 外）需刪除 branch

---

## ✅ 驗收標準（以 main 為準）

- 是否出現 X 軸（橫向捲動）
- 是否有破版或明顯視覺問題
- 路由是否正常
- 功能是否正確
- branch / commit / PR 命名是否一致
- 是否有重複命名的 branch 或 PR

---

## 📱 RWD 斷點規範（Tailwind 預設）

| Breakpoint | 寬度 |
| --- | --- |
| sm | < 768px |
| md | ≥ 768px |
| lg | ≥ 1024px |
| xl | ≥ 1280px |

---





## 📌 備註

- 若流程或規範需要調整，請先於 Notion 或 PR 中討論
- 本文件為團隊共識，請所有成員務必遵守


---
## 本地運行方式


### 1. 安裝相依套件

```bash
npm install
```

### **2. 啟動開發伺服器**

```bash
npm run dev
```
