# Classic ASP 跨瀏覽器現代化升級 Skill / Classic ASP Cross-Browser Modernization Skill

[繁體中文](#繁體中文) · [English](#english)

---

## 繁體中文

### Classic ASP 跨瀏覽器現代化升級 Skill

讓跑了 10–20 年的 Classic ASP 網站，在 **Chrome / Edge 完美呈現**，同時**保留 IE8 相容**，**後端一行程式都不用動**。

你有一批跑了十幾年的 Classic ASP 頁面。後端邏輯沒有問題，但前端在 Chrome 上跑版、JS 報錯、客戶開始抱怨。你知道該動了，但沒有人有把握「動了不會壞」。

這個 Skill 就是為了這件事存在的。

### 這個 Skill 做什麼

把升級規則、邊界限制、測試流程全部封存進 GitHub Copilot 的提示詞架構，讓每一次前端升級都從同一個起點出發，輸出品質不靠運氣。

- **現代瀏覽器優先**：Chrome / Edge 是主要品質標準，不是附加需求
- **IE8 向下相容**：透過通用語法與雙寫 fallback，兩者可以同時達成
- **後端零風險**：四條硬性邊界確保 VBScript 邏輯、表單欄位、AJAX 端點一字不動
- **26 條規則自動驗證**：每次升級完跑掃描腳本，品質可量化
- **可追溯的升級歷程**：`--confirm` 寫入確認記錄，`DEPLOYMENT.md` 自動累積佈署紀錄

### 快速開始

**1. 取得這個 Skill**

點右上角的 **Use this template** 建立你自己的副本，或直接 clone：

```bash
git clone https://github.com/你的帳號/classic-asp-copilot-skill.git
```

**2. 複製到你的 ASP 專案**

```bash
cp -r classic-asp-copilot-skill/. /你的專案目錄/
```

**3. 兩分鐘設定**

打開 `SETUP.md`，依指引調整兩個地方：

- **`copilot-instructions.md`**：填入你的專案副檔名（`.vs`、`.vbs` 等，預設只有 `.asp` / `.inc`）
- **`references/html-patterns.md`**：填入你的 jQuery 和 CSS 的實際路徑

**4. 開始第一次升級**

在 VS Code Copilot Chat 選 **Agent** 模式，輸入：

```
升級 your-page.asp 的前端，現代化優先，保持 IE8 向下相容
```

### 升級流程總覽

每一個 ASP 頁面，走完七步才算完成：

```
掃描 → 規劃 → 升級 → 靜態掃描（26 條規則）
     → 跨瀏覽器確認 → --confirm 寫入記錄 → 佈署詢問
```

每一步都有鎖鏈關係，前一步沒完成不能進下一步。

### 設計原則

**「不是降級，是選用通用子集。」**

不因為要支援 IE8 就限制自己用最舊的語法，而是選用在所有目標瀏覽器都正確運作的語法子集。同樣是 `var`，在 Chrome 和 IE8 都完全正常；`opacity: 0.8` 加上 `filter: alpha(opacity=80)` 兩行，現代瀏覽器用第一行，IE8 用第二行，沒有任何妥協。

### 適用情境

✅ 前端在 Chrome / Edge 顯示異常，後端穩定不需翻新
✅ 需要同時支援現代瀏覽器與 IE8
✅ 想讓升級過程有一致的品質標準與可追溯的紀錄
✅ 不打算（或還沒準備好）做 .NET Core 重寫

### 系統需求

| 工具 | 版本 |
|------|------|
| VS Code | 1.99 以上 |
| GitHub Copilot | 任何付費方案 |
| PowerShell | 5.1 以上（Windows 內建）|
| Node.js | 16 以上（選填，跨平台掃描備用）|

### 授權

[MIT License](LICENSE) — 可自由使用、修改、發佈。

---

## English

### Classic ASP Cross-Browser Modernization Skill

**GitHub Copilot Agent Skill · Modernize Classic ASP frontends for Chrome — zero backend risk**

You have a batch of Classic ASP pages that have been running for over a decade. The backend logic works fine, but the frontend breaks in Chrome — layout issues, JS errors, and customers starting to complain. You know it needs to be fixed, but nobody feels confident that touching it won't cause something else to break.

This Skill exists exactly for that situation.

### What This Skill Does

It encodes upgrade rules, hard boundaries, and testing workflows directly into GitHub Copilot's prompt architecture. Every upgrade starts from the same baseline, and output quality no longer depends on luck.

- **Modern browsers first**: Chrome / Edge is the primary quality standard, not an afterthought
- **IE8 backward compatibility**: achieved simultaneously through universal syntax and dual-write fallbacks
- **Zero backend risk**: four hard boundaries ensure VBScript logic, form fields, and AJAX endpoints are never touched
- **26 rules, automatically verified**: run the scan script after every upgrade — quality is measurable
- **Traceable upgrade history**: `--confirm` writes browser verification records; `DEPLOYMENT.md` accumulates deployment logs automatically

### Quick Start

**1. Get the Skill**

Click **Use this template** to create your own copy, or clone directly:

```bash
git clone https://github.com/your-account/classic-asp-copilot-skill.git
```

**2. Copy into your ASP project**

```bash
cp -r classic-asp-copilot-skill/. /your-project-directory/
```

**3. Two-minute setup**

Open `SETUP.md` and adjust two things:

- **`copilot-instructions.md`**: add your project's file extensions (`.vs`, `.vbs`, etc. — defaults to `.asp` / `.inc` only)
- **`references/html-patterns.md`**: replace placeholder paths with your actual jQuery and CSS paths

**4. Run your first upgrade**

In VS Code Copilot Chat, switch to **Agent** mode and type:

```
Upgrade the frontend of your-page.asp, modern browsers first, maintain IE8 backward compatibility
```

### Upgrade Workflow

Every ASP page follows the same seven steps before it's considered done:

```
Scan → Plan → Upgrade → Static scan (26 rules)
     → Cross-browser verification → --confirm → Deployment log
```

Each step is chained to the previous one — no skipping ahead.

### Design Philosophy

**"Not downgrading. Choosing a universal subset."**

The idea is not to restrict yourself to the oldest syntax just because IE8 needs support. Instead, choose the syntax subset that works correctly across all target browsers. `var` runs fine in both Chrome and IE8. Writing `opacity: 0.8` followed by `filter: alpha(opacity=80)` means modern browsers use the first line, IE8 uses the second — no compromises made.

### When to Use This

✅ Frontend broken in Chrome / Edge, but backend is stable and doesn't need rewriting
✅ Must support both modern browsers and IE8
✅ Need consistent quality standards and traceable records for every upgrade
✅ Not ready (or not planning) to do a .NET Core rewrite

### Requirements

| Tool | Version |
|------|---------|
| VS Code | 1.99 or later |
| GitHub Copilot | Any paid plan |
| PowerShell | 5.1 or later (built into Windows) |
| Node.js | 16 or later (optional, cross-platform scan alternative) |

### License

[MIT License](LICENSE) — free to use, modify, and distribute.

---

## File Structure / 檔案結構

```
.github/
├── copilot-instructions.md              ← Layer 1: always active / 每次對話自動生效
└── skills/
    └── classic-asp-frontend-upgrade/
        ├── SKILL.md                     ← Layer 2: loaded on demand / 按需載入
        └── references/
            ├── cross-browser-javascript.md   ← JS rules / 規則（12 + 4）
            ├── cross-browser-css.md          ← CSS strategy / 三類策略（6 + 2）
            ├── html-patterns.md              ← HTML patterns / 結構重組模式
            ├── testing.md                    ← Scan workflow / 掃描流程
            └── deployment-logging.md         ← Deployment log / 佈署紀錄格式

scripts/
├── test-compat.ps1                      ← Static scan (PowerShell / Windows)
└── test-compat.js                       ← Static scan (Node.js / cross-platform)

README.md        ← This file / 本檔案
SETUP.md         ← Setup guide / 安裝設定指引
QUICKSTART.md    ← Quick reference / 快速使用指南
DEPLOYMENT.md    ← Deployment log / 佈署紀錄（自動累積）
```
