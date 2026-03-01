# Classic ASP 跨瀏覽器現代化升級 Skill

**GitHub Copilot Agent Skill · 現代化優先 · 向下相容 IE8 · 後端零風險**

---

## 這個 Skill 做什麼

讓 GitHub Copilot 能夠系統性地升級 Classic ASP 頁面的前端，使頁面在 Chrome / Edge 等現代瀏覽器正確運作，同時維持對 IE8 的向下相容，且**完全不碰後端 VBScript 邏輯**。

- 26 條靜態掃描規則自動驗證每次升級的正確性
- 七步標準化流程確保品質可追溯
- `--confirm` 機制將跨瀏覽器手動確認結果寫入 MD 報告
- `DEPLOYMENT.md` 自動累積每頁升級的佈署歷程

---

## 適用對象

- 任何使用 Classic ASP（`.asp`）的系統
- 前端在 Chrome / Edge 顯示異常，但後端邏輯穩定不需翻新
- 需要同時支援現代瀏覽器與舊版 IE

---

## 檔案結構

```
.github/
├── copilot-instructions.md                    ← Layer 1：永遠生效，每次對話自動載入
└── skills/
    └── classic-asp-frontend-upgrade/
        ├── SKILL.md                           ← Layer 2：Skill 入口，按需載入
        └── references/
            ├── cross-browser-javascript.md    ← JS 升級規則與範例（26 條中的 16 條）
            ├── cross-browser-css.md           ← CSS 三類策略與範例（26 條中的 8 條）
            ├── html-patterns.md               ← HTML 結構重組模式（26 條中的 2 條）
            ├── testing.md                     ← 靜態掃描流程與修正對照表
            └── deployment-logging.md          ← 佈署紀錄格式與觸發規則

scripts/
├── test-compat.ps1                            ← 靜態掃描腳本（Windows PowerShell）
└── test-compat.js                             ← 靜態掃描腳本（Node.js 跨平台）

QUICKSTART.md                                  ← 快速使用指南
DEPLOYMENT.md                                  ← 佈署紀錄（自動累積，初始為空）
README.md                                      ← 本檔案
```

---

## 快速安裝（五分鐘）

### 1. 複製到你的專案

```bash
# 把整個目錄複製到你的 Classic ASP 專案根目錄
cp -r classic-asp-skill/. /your-project/
```

### 2. 依你的專案調整設定

複製後，打開 `SETUP.md` 依指引調整兩個地方：

- **`copilot-instructions.md`**：填入你的專案實際使用的副檔名
- **`references/html-patterns.md`**：填入你的 asset 路徑（jQuery、CSS 的實際路徑）

詳細說明見 [`SETUP.md`](./SETUP.md)。

### 3. 確認 Copilot Agent mode 已啟用

VS Code → Copilot Chat 面板右上角選 **Agent**

### 4. 開始第一次升級

```
升級 your-page.asp 的前端，現代化優先，保持 IE8 向下相容
```

---

## 需求

| 工具 | 版本需求 |
|------|---------|
| VS Code | 1.99 以上 |
| GitHub Copilot | 任何付費方案 |
| PowerShell（掃描） | 5.1 以上（Windows 內建）|
| Node.js（掃描，可選）| 16 以上 |

---

## 授權

MIT License — 可自由使用、修改、發佈，但請保留原始授權聲明。

---

## 版本

`v1.0.0` — 2026-03
