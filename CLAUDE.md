# appfortrip - 釜山旅行網站

**專案類型**：靜態旅行行程展示網站
**部署方式**：GitHub Pages
**網址**：https://axk1990.github.io/Busantrip/
**GitHub Repo**：https://github.com/AXK1990/Busantrip.git
**分支**：`master`（本地 `git init` 建立，不是 `main`）

---

## 🎯 專案定位

這是一個靜態 HTML 網站，用於展示 2026 年釜山六日美食探索之旅的完整行程規劃。

**特點**：
- 📱 手機優先設計（響應式）
- 🎨 優雅的視覺設計（海洋主題配色）
- 📍 Google Maps 整合（所有地點可直接導航）
- 🔤 字體大小控制（A-、A、A+）
- 📑 分頁設計（行程總覽、美食清單、交通資訊、注意事項）

**使用場景**：
- 旅行前查看完整行程
- 旅行中隨時查看當日安排
- 點擊地址直接開啟 Google Maps 導航
- 分享給同行友人

---

## 📁 檔案結構

```
appfortrip/
├── index.html          # 主網頁檔案（唯一的 HTML）
├── IMG_6237.jpeg       # 圖片素材
├── IMG_6238.jpeg       # 圖片素材
├── .gitignore          # Git 忽略規則
└── CLAUDE.md           # 本文件（專案指南）
```

**已排除**：`.txt` 草稿檔案（峇里島之旅.txt 等）

---

## 🏗️ 網站結構

### HTML 主要區塊

1. **Hero 區域**（`.hero`）
   - 標題：釜山六日美食探索之旅
   - 副標題：海景咖啡 × 韓式烤肉 × 文藝海岸
   - 旅行資訊 pills：日期、人數、住宿

2. **字體控制**（`.font-control`）
   - 三個按鈕：A-（小）、A（中）、A+（大）
   - 使用 localStorage 記住用戶偏好

3. **分頁導覽**（`.nav-tabs`）
   - Tab 1：行程總覽（預設顯示）
   - Tab 2：美食清單
   - Tab 3：交通資訊
   - Tab 4：注意事項

4. **行程總覽**（`#itinerary`）
   - 6 個 `.day-card`（Day 1-6）
   - 每天可展開/收合（點擊 `.day-header`）
   - Timeline 時間軸（`.timeline` → `.tl-item`）

5. **美食清單**（`#restaurants`）
   - 依區域分類（西面/田浦、南浦/影島、廣安里、海雲台等）
   - 每個餐廳含：名稱、類型、描述、Google Maps 連結

6. **交通資訊**（`#transport`）
   - 航班資訊（`.flight-card`）
   - 專車接送（KLOOK）
   - Uber 叫車說明
   - 住宿資訊（2 間）

7. **注意事項**（`#notes`）
   - 待辦事項 checklist
   - 實用資訊（天氣、電壓、時差等）

### JavaScript 功能

```javascript
showTab(id, btn)        // 切換分頁
toggleDay(card)         // 展開/收合行程卡片
setFontSize(size)       // 字體大小控制（small/medium/large）
```

### CSS 變數（`:root`）

```css
--ocean: #e8f3f7;       // 淺海洋藍（背景）
--sea: #d4e8ef;         // 海洋色（邊框）
--marine: #5b9aad;      // 海洋綠（強調色）
--deep: #1a3847;        // 深海藍（Hero 背景、深色文字）
--coral: #e86c5e;       // 珊瑚色（亮點色）
--sand: #f4e4d7;        // 沙色（提示框背景）
--font-scale: 1.0;      // 字體縮放比例（由字體控制調整）
```

---

## ✏️ 如何修改網站

### **檢視當前版本**

1. **線上版本**（推送後 5-10 分鐘生效）：
   https://axk1990.github.io/Busantrip/

2. **本地預覽**（即時修改查看）：
   ```bash
   # 直接在瀏覽器開啟檔案
   # Windows: 右鍵 index.html → 開啟方式 → Chrome/Edge
   # 或使用本地伺服器（推薦）：
   cd appfortrip
   python -m http.server 8000
   # 瀏覽器打開 http://localhost:8000
   ```

---

### **常見修改場景**

#### 1️⃣ 修改行程內容

**範例：修改 Day 2 的早餐時間和地點**

找到 Day 2 的 `.day-card`（Line 227-375），在 `.timeline` 內找到早餐的 `.tl-item`：

```html
<div class="tl-item">
  <div class="tl-time">早餐</div>  <!-- 修改時間 -->
  <div class="tl-dot"></div>
  <div class="tl-content">
    <div class="tl-title">西面/田浦商圈早餐</div>  <!-- 修改標題 -->
    <div class="tl-desc">
      推薦選項：<br>
      • SOUP or SALAD（西面）<br>  <!-- 修改內容 -->
      • Your Type Jeonpo（田浦商圈）
    </div>
    <div class="tl-links">
      <!-- 修改/新增 Google Maps 連結 -->
      <a class="ml" href="https://maps.google.com/?q=..." target="_blank">📍 地址</a>
    </div>
  </div>
</div>
```

#### 2️⃣ 新增一個行程項目

在對應 Day 的 `.timeline` 內，複製一個 `.tl-item` 區塊：

```html
<div class="tl-item">
  <div class="tl-time">14:00</div>  <!-- 時間 -->
  <div class="tl-dot hi"></div>  <!-- hi = 紅色圓點（重點行程），無 hi = 灰色 -->
  <div class="tl-content">
    <div class="tl-title">新增的景點名稱</div>
    <div class="tl-desc">景點描述，可使用 &lt;br&gt; 換行</div>
    <div class="tl-links">
      <a class="ml" href="https://maps.google.com/?q=新景點+Busan" target="_blank">📍 地址</a>
      <a class="wl" href="https://example.com" target="_blank">🌐 官網</a>
    </div>
  </div>
</div>
```

**重點說明**：
- `.tl-dot` - 普通行程項目
- `.tl-dot.hi` - 重點行程（紅色圓點）
- `.ml` - Google Maps 連結（藍色）
- `.wl` - 網站連結（橘色）

#### 3️⃣ 新增美食餐廳

在 `#restaurants` 區域，找到對應區域分類（如 `📍 西面 / 田浦`），新增 `.rest-item`：

```html
<div class="rest-item">
  <div class="rest-name">餐廳名稱</div>
  <div class="rest-desc">料理類型｜簡短描述</div>
  <div style="margin-top:6px;">
    <a class="ml" href="https://maps.google.com/?q=餐廳名稱+Busan" target="_blank">📍 地址</a>
  </div>
</div>
```

#### 4️⃣ 新增一整天行程

複製現有的 `.day-card`（整個區塊 Line 148-224），修改：
1. `.day-num` - 日期編號（01 → 07）
2. `.day-title` - 當日主題
3. `.day-date` - 日期和路線
4. `.timeline` 內的所有行程項目

#### 5️⃣ 修改 Uber 目的地名稱

找到 Uber 行程項目（Line 257-266 等），修改 `<code>` 標籤內的英文地名：

```html
<div class="tl-desc" style="background:var(--sand);padding:10px;border-radius:6px;margin-top:6px;">
  <strong>Uber 目的地（可複製）：</strong><br>
  <code style="background:white;padding:2px 6px;border-radius:3px;font-size:13px;display:inline-block;margin-top:4px;">
    New Destination Name  <!-- 修改這裡 -->
  </code>
</div>
```

#### 6️⃣ 修改待辦事項 Checklist

在 `#notes` Tab（Line 1098-1109），修改 checklist：

```html
<!-- 未完成 -->
☐ 新增待辦事項<br>

<!-- 已完成（綠色標記）-->
<span style="color:var(--marine);font-weight:500;">✓ 已完成項目</span><br>
```

---

## 🚀 部署流程

### **標準更新流程**

```bash
cd appfortrip

# 1. 修改 index.html（使用 Claude Code 的 Edit 工具）

# 2. 提交變更
git add .
git commit -m "更新行程：[簡短描述修改內容]"

# 3. 推送到 GitHub
git push

# 4. 等待 5-10 分鐘，GitHub Pages 自動部署
```

### **驗證部署**

```bash
# 檢查推送狀態
git log -1 --oneline

# 打開網址檢查（5-10 分鐘後）
# https://axk1990.github.io/Busantrip/
```

---

## ⚙️ 注意事項

### **分支名稱**
- ⚠️ 這個 repo 的分支是 `master`（不是 `main`）
- 原因：本地 `git init` 建立的 repo，預設分支為 `master`
- 推送指令：`git push`（已設定 tracking，會自動推送到 master）

### **圖片檔案**
- 圖片檔案（`IMG_*.jpeg`）已納入 git，需一起提交
- 新增圖片時記得 `git add` 並推送

### **HTML 結構一致性**
- 保持 `.tl-item`、`.rest-item`、`.card` 等結構一致
- 複製現有區塊修改，避免破壞樣式

### **Google Maps 連結格式**
```
https://maps.google.com/?q=地點名稱+Busan
```
- 使用 `+` 連接多個詞（空格會自動轉換）
- 建議加上 `Busan` 確保定位正確

---

## 🎓 快速開始（給未來的 Claude）

**當用戶要求修改 appfortrip 網站時：**

1. **讀取當前版本**
   ```bash
   cd appfortrip
   # 讀取 index.html（了解當前內容）
   ```

2. **檢視線上版本**（可選）
   - 在瀏覽器打開：https://axk1990.github.io/Busantrip/
   - 了解當前網站狀態和用戶體驗

3. **根據用戶需求修改**
   - 使用 Edit 工具修改 `index.html`
   - 參考上方「如何修改網站」章節的範例

4. **推送並告知用戶**
   ```bash
   git add .
   git commit -m "更新：[描述]"
   git push
   ```
   告訴用戶：「已推送，5-10 分鐘後生效，請重新整理網頁」

---

## 📞 常見問題

**Q: 如何在本地即時預覽修改？**
A: 使用 `python -m http.server 8000` 啟動本地伺服器，或直接用瀏覽器開啟 `index.html`

**Q: 推送後網站沒更新？**
A: GitHub Pages 需要 5-10 分鐘建置，耐心等待。可到 repo 的 Actions 頁面查看部署狀態。

**Q: 如何新增一個分頁（Tab）？**
A:
1. 在 `.nav-tabs` 新增 `<button class="tab-btn" onclick="showTab('new-tab',this)">新分頁</button>`
2. 在 `.container` 內新增 `<div id="new-tab" class="section">內容</div>`

**Q: 如何修改配色？**
A: 修改 `:root` 內的 CSS 變數（Line 9-16）

---

**維護者**：Claude Code (Sonnet 4.5)
**建立日期**：2026-08-02
**最後更新**：2026-08-02
