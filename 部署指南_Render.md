# 🚀 Render 部署指南

## 📋 部署前準備

### 1. 註冊 Render 帳號
1. 前往 [Render.com](https://render.com/)
2. 點擊右上角 "Get Started"
3. 使用 GitHub 帳號註冊（推薦）或使用 Email 註冊
4. 驗證您的 Email

### 2. 準備 GitHub 倉庫
1. 前往 [GitHub.com](https://github.com/)
2. 創建新倉庫（New Repository）
3. 倉庫名稱：`yao-medicine-app`
4. 設為 Public（公開）
5. 不要勾選 "Initialize this repository with a README"

## 📤 上傳代碼到 GitHub

### 方法 1：使用終端機（推薦）

```bash
# 1. 在您的專案目錄中初始化 Git
cd /Users/zzzzzzzs/Desktop/yao
git init

# 2. 添加 .gitignore 文件（避免上傳敏感資料）
echo "node_modules/" > .gitignore
echo ".env" >> .gitignore
echo ".DS_Store" >> .gitignore
echo "*.log" >> .gitignore

# 3. 添加所有文件
git add .

# 4. 提交
git commit -m "Initial commit"

# 5. 連接到您的 GitHub 倉庫（替換成您的 GitHub 用戶名）
git remote add origin https://github.com/您的用戶名/yao-medicine-app.git

# 6. 推送到 GitHub
git branch -M main
git push -u origin main
```

### 方法 2：使用 GitHub Desktop（簡單）

1. 下載並安裝 [GitHub Desktop](https://desktop.github.com/)
2. 登入您的 GitHub 帳號
3. File → Add Local Repository → 選擇 `/Users/zzzzzzzs/Desktop/yao`
4. 點擊 "Publish repository"
5. 確認倉庫名稱為 `yao-medicine-app`
6. 點擊 "Publish Repository"

## 🌐 在 Render 上部署

### 步驟 1：部署後端 API

1. **登入 Render**
   - 前往 [dashboard.render.com](https://dashboard.render.com/)
   - 使用 GitHub 登入

2. **創建新的 Web Service**
   - 點擊右上角 "New +" 按鈕
   - 選擇 "Web Service"

3. **連接 GitHub 倉庫**
   - 選擇 "Connect a repository"
   - 找到並選擇 `yao-medicine-app`
   - 點擊 "Connect"

4. **配置後端服務**
   ```
   Name: yao-backend
   Region: Singapore (或選擇最近的地區)
   Branch: main
   Root Directory: server
   Runtime: Node
   Build Command: npm install
   Start Command: node server.js
   Instance Type: Free
   ```

5. **設置環境變數**
   - 在頁面下方找到 "Environment Variables"
   - 點擊 "Add Environment Variable"
   - 添加以下變數：
     ```
     Key: GEMINI_API_KEY
     Value: AIzaSyDUEPDseVw_3SsivkFI2IwpKsIgcsgsm9g
     ```
   - 添加第二個變數：
     ```
     Key: NODE_ENV
     Value: production
     ```

6. **創建服務**
   - 點擊 "Create Web Service"
   - 等待部署完成（約 3-5 分鐘）
   - 部署成功後，您會看到一個網址，例如：
     `https://yao-backend.onrender.com`
   - **記下這個網址！**

### 步驟 2：部署前端網站

1. **創建新的 Static Site**
   - 回到 Render Dashboard
   - 點擊 "New +" → "Static Site"

2. **連接同一個 GitHub 倉庫**
   - 選擇 `yao-medicine-app`
   - 點擊 "Connect"

3. **配置前端服務**
   ```
   Name: yao-frontend
   Branch: main
   Root Directory: (留空)
   Build Command: (留空)
   Publish Directory: wangya
   ```

4. **創建服務**
   - 點擊 "Create Static Site"
   - 等待部署完成（約 1-2 分鐘）
   - 部署成功後，您會看到前端網址，例如：
     `https://yao-frontend.onrender.com`

### 步驟 3：更新前端 API 網址

1. **修改 index.html**
   - 打開 `wangya/index.html`
   - 找到第 4466 行：
     ```javascript
     const API_BASE_URL = 'http://localhost:3000';
     ```
   - 改為您的後端網址：
     ```javascript
     const API_BASE_URL = 'https://yao-backend.onrender.com';
     ```

2. **重新上傳到 GitHub**
   ```bash
   git add wangya/index.html
   git commit -m "Update API URL for production"
   git push
   ```

3. **Render 會自動重新部署**
   - 前端會自動檢測到代碼更新
   - 等待 1-2 分鐘重新部署完成

## ✅ 完成！

### 🎉 您的網站現在可以全球訪問了！

**前端網址**：`https://yao-frontend.onrender.com`  
**後端網址**：`https://yao-backend.onrender.com`

任何人都可以通過前端網址使用您的藥品管理系統和 AI 諮詢功能！

## 🔧 常見問題

### Q1: 第一次訪問很慢？
**A**: Render 免費版會在 15 分鐘無活動後進入休眠。第一次訪問需要 30 秒左右喚醒。

**解決方法**：
- 使用 [UptimeRobot](https://uptimerobot.com/) 每 10 分鐘 ping 一次您的網站
- 或升級到付費版本（每月 $7 美金）

### Q2: 如何更新網站？
**A**: 只需要推送代碼到 GitHub，Render 會自動重新部署：
```bash
git add .
git commit -m "Update features"
git push
```

### Q3: 如何查看後端日誌？
**A**: 
1. 登入 Render Dashboard
2. 選擇 `yao-backend`
3. 點擊左側 "Logs" 標籤
4. 可以看到即時日誌輸出

### Q4: 免費版有什麼限制？
**A**:
- ✅ 無限制的部署次數
- ✅ 自動 SSL 證書（HTTPS）
- ⚠️ 750 小時/月的運行時間（足夠個人使用）
- ⚠️ 15 分鐘無活動後休眠
- ⚠️ 100GB 流量/月

### Q5: 如何保護 API 密鑰？
**A**: 
- ✅ 密鑰存儲在 Render 的環境變數中，不會暴露
- ✅ 前端代碼不包含密鑰
- ✅ 所有 API 調用通過後端代理

## 📱 分享給其他人

部署完成後，您可以將前端網址分享給任何人：

**網址**：`https://yao-frontend.onrender.com`

他們只需要：
1. 打開瀏覽器
2. 輸入網址
3. 立即使用！

不需要：
- ❌ 下載任何東西
- ❌ 安裝任何軟體
- ❌ 在同一個網路
- ❌ 您的電腦開著

## 🎓 進階選項

### 自訂域名（可選）

如果您有自己的域名（例如 `medicine.example.com`）：

1. 在 Render Dashboard 中選擇您的服務
2. 點擊 "Settings" → "Custom Domain"
3. 輸入您的域名
4. 在域名提供商處設置 CNAME 記錄
5. 等待 DNS 生效（通常幾分鐘到 24 小時）

### 監控與分析

1. **Render Analytics**
   - 自動提供基本的流量統計
   - 可以看到請求數、回應時間等

2. **Google Analytics**（可選）
   - 如果想要更詳細的使用統計
   - 可以在 `index.html` 中添加 Google Analytics 代碼

## 📞 需要幫助？

- **Render 文檔**: [docs.render.com](https://docs.render.com/)
- **Render 社群**: [community.render.com](https://community.render.com/)
- **GitHub 幫助**: [docs.github.com](https://docs.github.com/)

---

**恭喜！🎊 您的應用現在已經在雲端運行了！**

