# 🗺️ 如何更新 Google Maps 嵌入代碼

## 📋 已加入地圖的店家

目前已為以下店家加入 Google Maps 嵌入容器（使用示範連結）：

1. **VISTA** - Pattaya Soi 4
2. **Siam** - 近哈尼和好好大浴室
3. **The Grass** - 對面168土嗨吧
4. **HONEY BODY MASSAGE（哈尼）** - 大浴室
5. **好好大浴室（中心浴室）**

---

## 🔧 如何取得真實的 Google Maps 嵌入代碼

### 步驟 1：在 Google Maps 找到店家

1. 打開 [Google Maps](https://www.google.com/maps)
2. 搜尋店家名稱（例如：「Vista Hotel Pattaya Soi 4」）
3. 確認找到正確的店家

### 步驟 2：取得嵌入代碼

1. 點選店家卡片上的 **「分享」** 按鈕
2. 選擇 **「嵌入地圖」** 分頁
3. 選擇地圖大小（建議：中等或大型）
4. 點選 **「複製 HTML」**

### 步驟 3：替換 index.html 中的代碼

1. 開啟 `index.html`
2. 找到對應店家的 `<div class="venue-map">` 區塊
3. 用剛複製的嵌入代碼替換現有的 `<iframe>` 標籤

**範例（替換前）：**
```html
<div class="venue-map">
    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!..." 
            allowfullscreen="" 
            loading="lazy" 
            referrerpolicy="no-referrer-when-downgrade">
    </iframe>
</div>
```

**範例（替換後）：**
```html
<div class="venue-map">
    <!-- 貼上 Google Maps 複製的 iframe 代碼 -->
    <iframe src="真實的Google Maps嵌入連結..." 
            width="600" 
            height="450" 
            style="border:0;" 
            allowfullscreen="" 
            loading="lazy" 
            referrerpolicy="no-referrer-when-downgrade">
    </iframe>
</div>
```

---

## 🎯 快速更新指令（電腦操作）

### 方法 1：手動編輯（最簡單）

1. 用文字編輯器打開 `~/.openclaw/workspace/pattaya-guide/index.html`
2. 搜尋店家名稱（例如：`VISTA`）
3. 找到下方的 `<div class="venue-map">` 區塊
4. 替換 iframe 的 `src` 連結
5. 儲存檔案
6. 提交到 GitHub：

```bash
cd ~/.openclaw/workspace/pattaya-guide
git add index.html
git commit -m "更新 Google Maps 真實嵌入連結"
git push origin main
```

---

## 📝 店家 Google Maps 搜尋建議

| 店家名稱 | 建議搜尋關鍵字 |
|---------|-------------|
| VISTA | Vista Hotel Pattaya Soi 4 |
| Siam | Siam@Siam Design Hotel Pattaya |
| The Grass | The Grass Serviced Suites Pattaya |
| 哈尼 | Honey Body Massage Pattaya |
| 好好大浴室 | Center Massage Pattaya |

---

## ⚡ 批次更新腳本（進階）

如果你想一次更新所有地圖，可以使用以下 Node.js 腳本：

```javascript
// update-maps.js（範例）
const fs = require('fs');

const maps = {
  'VISTA': 'https://www.google.com/maps/embed?pb=真實連結1',
  'Siam': 'https://www.google.com/maps/embed?pb=真實連結2',
  'The Grass': 'https://www.google.com/maps/embed?pb=真實連結3',
  // ... 其他店家
};

let html = fs.readFileSync('index.html', 'utf8');

Object.entries(maps).forEach(([name, url]) => {
  // 替換邏輯（需要根據實際 HTML 結構調整）
  const regex = new RegExp(`(<div class="venue-name">${name}</div>.*?<iframe src=").*?(">)`, 's');
  html = html.replace(regex, `$1${url}$2`);
});

fs.writeFileSync('index.html', html);
console.log('✅ 地圖更新完成！');
```

執行：
```bash
node update-maps.js
```

---

## 🔍 驗證地圖是否正常

更新後，打開網站確認：

1. 地圖是否正確顯示
2. 位置是否正確
3. 手機版是否正常顯示

---

## 💡 注意事項

1. **版權合法性**：Google Maps 嵌入是官方功能，完全合法 ✅
2. **載入速度**：地圖會稍微增加頁面載入時間，但在可接受範圍內
3. **自動更新**：Google Maps 會自動更新店家資訊、評論、照片
4. **手機體驗**：地圖在手機上可以直接打開 Google Maps App

---

## 🆘 需要幫助？

如果不確定如何操作，可以：

1. 讓我（AI 助理）幫你自動更新
2. 提供店家名稱，我幫你找 Google Maps 連結
3. 一步步指導你操作

---

**更新完成後記得推送到 GitHub，網站會自動更新！** 🎉
