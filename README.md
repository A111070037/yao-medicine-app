# 🏥 藥嚀管 - 智能藥品管理系統

一個功能完整的藥品管理和健康諮詢系統，包含 AI 諮詢、藥品識別、健康記錄管理等功能。

## ✨ 主要功能

### 💊 藥品管理
- 📝 添加、編輯、刪除藥品資訊
- 📷 拍照識別藥品（使用 TensorFlow.js）
- ⏰ 服藥提醒和記錄
- 📊 庫存管理

### 🤖 AI 健康諮詢
- 💬 即時 AI 健康諮詢（使用 Gemini API）
- 🩺 專業的醫療建議
- 🇹🇼 繁體中文支持
- 🔒 健康相關問題過濾

### 📈 健康記錄
- 📉 血壓、血糖、心率等健康數據記錄
- 📊 數據可視化圖表
- 📄 PDF 報告匯出
- 📱 用藥記錄同步

### 🗺️ 附近醫療
- 📍 查找附近的藥局、醫院、診所
- 🔍 多種醫療類別篩選
- 🧭 一鍵導航和聯繫
- ⭐ 收藏常用醫療機構

## 🚀 快速開始

### 本地開發

#### 1. 安裝依賴
```bash
cd server
npm install
```

#### 2. 設置環境變數
創建 `server/.env` 文件：
```
GEMINI_API_KEY=your_gemini_api_key_here
PORT=3000
```

#### 3. 啟動後端服務器
```bash
cd server
npm start
```

#### 4. 打開前端
直接打開 `wangya/index.html` 文件即可使用。

## 🌐 部署到雲端

### 使用 Render（推薦，免費）

完整的部署指南請查看：**[部署指南_Render.md](./部署指南_Render.md)**

#### 快速部署步驟：

1. **準備 GitHub 倉庫**
   ```bash
   # 運行快速部署腳本
   ./快速部署.sh
   
   # 或手動執行
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/你的用戶名/yao-medicine-app.git
   git push -u origin main
   ```

2. **部署後端**
   - 前往 [Render Dashboard](https://dashboard.render.com/)
   - New + → Web Service
   - 連接 GitHub 倉庫
   - 配置：
     - Root Directory: `server`
     - Build Command: `npm install`
     - Start Command: `node server.js`
   - 添加環境變數：`GEMINI_API_KEY`

3. **部署前端**
   - New + → Static Site
   - 連接同一個倉庫
   - Publish Directory: `wangya`

4. **更新 API 網址**
   - 編輯 `wangya/index.html`
   - 將 `API_BASE_URL` 改為後端網址
   - 推送更新到 GitHub

✅ 完成！您的網站現在可以全球訪問！

## 📱 技術棧

### 前端
- HTML5 / CSS3 / JavaScript
- TensorFlow.js（藥品識別）
- Leaflet（地圖功能）
- Chart.js（數據可視化）
- html2pdf.js（PDF 匯出）

### 後端
- Node.js / Express
- Gemini API（AI 諮詢）
- Axios（HTTP 請求）

## 🔑 獲取 API 密鑰

### Gemini API
1. 前往 [Google AI Studio](https://makersuite.google.com/app/apikey)
2. 點擊 "Get API Key"
3. 創建新的 API 金鑰
4. 複製金鑰並保存

## 📖 使用說明

### 藥品管理
1. 點擊 "+" 按鈕添加藥品
2. 填寫藥品資訊（名稱、劑量、庫存等）
3. 設置服用時段
4. 上傳藥品照片（可選）

### AI 諮詢
1. 點擊底部 "AI諮詢" 標籤
2. 輸入健康相關問題
3. 獲得專業的 AI 回答
4. 重要問題請諮詢專業醫生

### 健康記錄
1. 點擊底部 "健康紀錄" 標籤
2. 選擇記錄類型（血壓、血糖等）
3. 點擊 "+" 添加新記錄
4. 查看趨勢圖表和歷史記錄

### 附近醫療
1. 點擊底部 "附近醫療" 標籤
2. 選擇醫療類別（藥局、醫院等）
3. 調整搜尋範圍
4. 點擊醫療機構查看詳情和導航

## 🛠️ 常見問題

### Q: AI 沒有回應？
**A**: 
- 檢查後端服務器是否運行
- 檢查 GEMINI_API_KEY 是否正確設置
- 查看瀏覽器控制台的錯誤訊息

### Q: 地圖載入很慢？
**A**: 
- 選擇較小的搜尋範圍（500米或1公里）
- 選擇單一類別而非"全部"
- 網路慢時會自動顯示提示

### Q: 如何備份數據？
**A**: 
- 所有數據儲存在瀏覽器 LocalStorage
- 使用瀏覽器的匯出功能
- 或複製 LocalStorage 數據

## 📄 授權

此專案僅供學習和個人使用。

## 🙏 致謝

- [Google Gemini API](https://ai.google.dev/)
- [TensorFlow.js](https://www.tensorflow.org/js)
- [Leaflet](https://leafletjs.com/)
- [Chart.js](https://www.chartjs.org/)
- [OpenStreetMap](https://www.openstreetmap.org/)

## 📞 聯繫

如有問題或建議，歡迎提出 Issue。

---

**Made with ❤️ for better health management**

