# classic-asp-copilot-skill
GitHub Copilot Agent Skill for Classic ASP cross-browser modernization

# Classic ASP 跨瀏覽器現代化升級 Skill

**GitHub Copilot Agent Skill · 讓舊系統在 Chrome 正常跑，後端一行不動**

---

你有一批跑了十幾年的 Classic ASP 頁面。後端邏輯沒有問題，但前端在 Chrome 上跑版、JS 報錯、客戶開始抱怨。你知道該動了，但沒有人有把握「動了不會壞」。

這個 Skill 就是為了這件事存在的。

---

## 這個 Skill 做什麼

把升級規則、邊界限制、測試流程全部封存進 GitHub Copilot 的提示詞架構，讓每一次前端升級都從同一個起點出發，輸出品質不靠運氣。

- **現代瀏覽器優先**：Chrome / Edge 是主要品質標準，不是附加需求
- **IE8 向下相容**：透過通用語法與雙寫 fallback，兩者可以同時達成
- **後端零風險**：四條硬性邊界確保 VBScript 邏輯、表單欄位、AJAX 端點一字不動
- **26 條規則自動驗證**：每次升級完跑掃描腳本，品質可量化
- **可追溯的升級歷程**：`--confirm` 寫入確認記錄，`DEPLOYMENT.md` 自動累積佈署紀錄

---

## 快速開始

### 1. 取得這個 Skill

點右上角的 **Use this template** 建立你自己的副本，或直接 clone：

```bash
git clone https://github.com/你的帳號/classic-asp-copilot-skill.git
```

### 2. 複製到你的 ASP 專案

```bash
cp -r classic-asp-copilot-skill/. /你的專案目錄/
```

### 3. 兩分鐘設定

打開 `SETUP.md`，依指引調整兩個地方：

- **`copilot-instructions.md`**：填入你的專案副檔名（`.vs`、`.vbs` 等，預設只有 `.asp` / `.inc`）
- **`references/html-patterns.md`**：填入你的 jQuery 和 CSS 的實際路徑

### 4. 開始第一次升級

在 VS Code Copilot Chat 選 **Agent** 模式，輸入：

```
升級 your-page.asp 的前端，現代化優先，保持 IE8 向下相容
```

---

## 檔案結構

```
.github/
├── copilot-instructions.md              ← Layer 1：每次對話自動生效
└── skills/
    └── classic-asp-frontend-upgrade/
        ├── SKILL.md                     ← Layer 2：按需載入
        └── references/
            ├── cross-browser-javascript.md   ← JS 升級規則（12 條合規 + 4 條回歸）
            ├── cross-browser-css.md          ← CSS 三類策略（6 條合規 + 2 條回歸）
            ├── html-patterns.md              ← HTML 結構重組模式
            ├── testing.md                    ← 掃描流程與修正對照表
            └── deployment-logging.md         ← 佈署紀錄格式

scripts/
├── test-compat.ps1                      ← 靜態掃描腳本（Windows PowerShell）
└── test-compat.js                       ← 靜態掃描腳本（Node.js 跨平台）

README.md          ← 本檔案
SETUP.md           ← 安裝設定指引
QUICKSTART.md      ← 快速使用指南
DEPLOYMENT.md      ← 佈署紀錄（自動累積）
```

---

## 升級流程總覽

每一個 ASP 頁面，走完七步才算完成：

```
掃描 → 規劃 → 升級 → 靜態掃描（26 條規則）
     → 跨瀏覽器確認 → --confirm 寫入記錄 → 佈署詢問
```

每一步都有鎖鏈關係，前一步沒完成不能進下一步。

---

## 設計原則

**「不是降級，是選用通用子集。」**

這個 Skill 的核心思維是：不因為要支援 IE8 就限制自己用最舊的語法，而是選用在所有目標瀏覽器都正確運作的語法子集。同樣是 `var`，在 Chrome 和 IE8 都完全正常；同樣是 `function(){}`，比箭頭函數多打幾個字，但兩邊都跑得動。

CSS 也是一樣的邏輯。`opacity: 0.8` 加上 `filter: alpha(opacity=80)` 兩行，現代瀏覽器用第一行，IE8 用第二行，沒有任何妥協。

---

## 系統需求

| 工具 | 版本 |
|------|------|
| VS Code | 1.99 以上 |
| GitHub Copilot | 任何付費方案 |
| PowerShell | 5.1 以上（Windows 內建，執行掃描腳本用）|
| Node.js | 16 以上（選填，跨平台掃描備用）|

---

## 適用情境

✅ 前端在 Chrome / Edge 顯示異常，後端穩定不需翻新
✅ 需要同時支援現代瀏覽器與 IE8
✅ 想讓升級過程有一致的品質標準與可追溯的紀錄
✅ 不打算（或還沒準備好）做 .NET Core 重寫

---

## 授權

[MIT License](LICENSE) — 可自由使用、修改、發佈。
