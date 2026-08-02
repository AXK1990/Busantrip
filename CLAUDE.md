# appfortrip - 釜山旅行網站

**網址**：https://axk1990.github.io/Busantrip/
**分支**：`master`（本地 git init 建立）
**GitHub**：https://github.com/AXK1990/Busantrip.git

靜態 HTML 旅行行程網站，手機優先設計，展示釜山六日美食探索之旅。

---

## 📁 主要檔案

- `index.html` - 主網頁（唯一 HTML）
- `IMG_*.jpeg` - 圖片素材
- `.gitignore` - 排除 `.txt` 草稿檔

---

## 🏗️ 網站結構

```
Hero 區域（標題、日期、住宿資訊）
  ↓
字體控制（A-、A、A+）
  ↓
分頁導覽（行程總覽、美食清單、交通資訊、注意事項）
  ↓
各分頁內容
```

**行程總覽**：6 個 `.day-card`，每天可展開/收合，內含 `.timeline` 時間軸
**美食清單**：依區域分類的 `.rest-item`
**交通資訊**：`.flight-card`（航班）+ 住宿資訊
**注意事項**：待辦 checklist + 實用資訊

---

## 🚀 快速開始（無上下文接手）

### 用戶要修改網站時：

1. **讀取當前版本**
   ```bash
   cd appfortrip
   # 讀取 index.html 了解結構
   ```

2. **檢視線上版本**（可選）
   - 網址：https://axk1990.github.io/Busantrip/
   - 了解當前網站狀態

3. **修改 index.html**
   - 使用 Edit 工具修改
   - 參考下方常見操作

4. **推送**
   ```bash
   git add .
   git commit -m "更新：[描述]"
   git push
   ```
   告知用戶：「已推送，5-10 分鐘後生效，請重新整理網頁」

---

## ✏️ 最常見操作

### 1. 修改行程時間/內容

找到對應 Day 的 `.day-card`（搜尋「Day 2」等），在 `.timeline` 內找到對應的 `.tl-item`：

```html
<div class="tl-item">
  <div class="tl-time">14:00</div>  <!-- 修改時間 -->
  <div class="tl-dot hi"></div>  <!-- hi=紅點(重點), 無=灰點 -->
  <div class="tl-content">
    <div class="tl-title">景點名稱</div>  <!-- 修改標題 -->
    <div class="tl-desc">描述內容</div>  <!-- 修改描述 -->
  </div>
</div>
```

### 2. 新增行程項目

複製一個 `.tl-item` 區塊，修改內容，插入到對應位置。

### 3. 新增美食餐廳

在 `#restaurants` 區域，找到對應區域分類（如「📍 西面 / 田浦」），新增：

```html
<div class="rest-item">
  <div class="rest-name">餐廳名稱</div>
  <div class="rest-desc">料理類型｜簡短描述</div>
  <div style="margin-top:6px;">
    <a class="ml" href="https://maps.google.com/?q=餐廳名稱+Busan" target="_blank">📍 地址</a>
  </div>
</div>
```

### 4. 修改 Uber 目的地

搜尋「Uber 目的地」，修改 `<code>` 內的英文地名。

---

## 🔧 注意事項

- **分支名稱**：`master`（不是 `main`），推送用 `git push`
- **部署時間**：GitHub Pages 需 5-10 分鐘建置
- **Google Maps 連結**：`https://maps.google.com/?q=地點名稱+Busan`
- **連結樣式**：`.ml` 藍色（地圖）、`.wl` 橘色（官網）
- **重點行程**：`.tl-dot.hi` 紅色圓點，`.tl-dot` 灰色圓點

---

**維護者**：Claude Code (Sonnet 4.5)
**建立日期**：2026-08-02
**最後更新**：2026-08-02
