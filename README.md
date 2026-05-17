# Global Markets Weekly Recap — 每週更新操作手冊

每週發布新報告時，需要依序完成以下三個步驟。

---

## 每週更新步驟

### 步驟一：上傳新的週報 HTML 檔

1. 進入 GitHub repo 首頁
2. 點進 `reports/` 資料夾
3. 點右上角 **Add file → Upload files**
4. 上傳新的週報 HTML 檔，命名格式為 `YYYY-MM-DD.html`（以該週最後一個交易日的日期為準，例如 `2026-05-15.html`）
5. 頁面下方填寫 commit 訊息（例如 `Add 2026-05-15 weekly report`），然後按 **Commit changes**

---

### 步驟二：更新 `index.html`（首頁自動跳轉）

`index.html` 的作用是讓首頁自動跳轉到最新週報。每次有新週報就要把日期改掉。

1. 在 repo 首頁點 `index.html`
2. 點右上角的鉛筆圖示（Edit this file）
3. 找到這一行：
   ```html
   <meta http-equiv="refresh" content="0; url=reports/2026-05-01.html">
   ```
   改成新的日期，例如：
   ```html
   <meta http-equiv="refresh" content="0; url=reports/2026-05-15.html">
   ```
4. 同樣找到這一行並更新：
   ```html
   <p>跳轉中... <a href="reports/2026-05-01.html">點此進入最新週報</a></p>
   ```
   改成：
   ```html
   <p>跳轉中... <a href="reports/2026-05-15.html">點此進入最新週報</a></p>
   ```
5. 點 **Commit changes**，直接 commit to main

---

### 步驟三：更新 `archive.html`（週報清單頁）

`archive.html` 是所有週報的目錄，需要做兩件事：**把舊的「最新」改為普通卡片，並新增本週卡片**。

1. 在 repo 首頁點 `archive.html`
2. 點右上角鉛筆圖示（Edit this file）

#### 3a. 把上週的「最新」卡片改為普通卡片

找到帶有 `class="report-card latest"` 的那張卡片：
```html
<a class="report-card latest" href="reports/2026-05-01.html">
```
把 `latest` 移除，改成：
```html
<a class="report-card" href="reports/2026-05-01.html">
```
並刪除卡片內的 `<span class="latest-badge">最新</span>` 這一行。

#### 3b. 在清單最上方新增本週卡片

在 `<div class="report-list">` 下方，緊接著加入新卡片（**複製以下模板並填入本週資訊**）：

```html
<!-- Latest -->
<a class="report-card latest" href="reports/2026-05-15.html">
  <div class="report-date">May 11–15</div>
  <div>
    <div class="report-title">【本週標題】</div>
    <div class="report-subtitle">【本週副標題：1-2 個重點事件】</div>
  </div>
  <div class="report-tags">
    <span class="latest-badge">最新</span>
    <span class="api-badge">✓ API</span>
    <span class="tag tag-us">🇺🇸</span>
    <span class="tag tag-eu">🇪🇺</span>
    <span class="tag tag-asia">🌏</span>
  </div>
  <div class="report-arrow">›</div>
</a>
```

#### 3c. 更新右上角「最新週報」連結

找到 header 中的這一行：
```html
<a href="reports/2026-05-01.html">→ 最新週報</a>
```
改成：
```html
<a href="reports/2026-05-15.html">→ 最新週報</a>
```

3. 完成後點 **Commit changes**

---

## 日期命名規則

| 欄位 | 格式 | 範例 |
|------|------|------|
| 檔案名稱 | `YYYY-MM-DD.html`（週五日期） | `2026-05-15.html` |
| `report-date` 顯示 | `Mon DD–DD`（週一至週五） | `May 11–15` |
| href 路徑 | `reports/YYYY-MM-DD.html` | `reports/2026-05-15.html` |

---

## 檔案結構說明

```
weekly-market-recap/
├── index.html        # 首頁，自動跳轉到最新週報（每週更新日期）
├── archive.html      # 所有週報的清單目錄（每週新增一張卡片）
├── README.md         # 本操作手冊
└── reports/
    ├── 2026-05-15.html   # 最新週報
    ├── 2026-05-01.html
    ├── 2026-04-24.html
    └── ...               # 歷史週報（不需動）
```

---

## 快速清單（每週 checklist）

- [ ] 上傳 `reports/YYYY-MM-DD.html`
- [ ] 更新 `index.html` 中的日期（2處）
- [ ] 更新 `archive.html` 中的「最新」卡片 → 改為普通卡片
- [ ] 在 `archive.html` 頂部新增本週「最新」卡片
- [ ] 更新 `archive.html` header 中的「最新週報」連結
