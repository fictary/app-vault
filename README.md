# 📱 App Vault — GitHub Pages 部署教學

從零到 iPhone 桌面 App，逐步操作指南。整個流程約 15 分鐘。

---

## 📦 你會用到的檔案

部署資料夾裡有 5 個檔案：

| 檔案 | 用途 |
|------|------|
| `index.html` | 主程式（單一檔案包含全部功能） |
| `manifest.json` | PWA 設定（讓 iPhone 認得這是 App） |
| `sw.js` | 離線快取（無網路也能用） |
| `icon-192.png` | App 圖示（小） |
| `icon-512.png` | App 圖示（大，主畫面用） |

---

## 步驟 1：註冊 GitHub 帳號 ⏱️ 3 分鐘

1. 用手機或電腦瀏覽器打開 👉 **https://github.com/signup**
2. 依序填寫：
   - **Email**：你常用的 email
   - **Password**：設定一組密碼（至少 8 字元含字母數字）
   - **Username**：取一個英文用戶名（例如 `john1234`），這會出現在你的網址裡
3. 收驗證碼信，輸入後完成註冊
4. 跳過 GitHub 問你的「想做什麼」「團隊規模」等問卷（隨便點過即可）

✅ 完成後你會看到 GitHub 主頁

---

## 步驟 2：建立倉庫 (Repository) ⏱️ 2 分鐘

倉庫 = 你的網站專案資料夾。

1. 登入後右上角點 **「+」** → **「New repository」**
2. 填寫設定：
   - **Repository name**：`app-vault`（要小寫，這會變成網址的一部分）
   - **Description**：可填可不填，例如 "我的 App 整理工具"
   - **Public** ✅（必須選公開，免費版才能用 Pages）
   - 其他選項**不要勾**（不要勾 README、不要 .gitignore、不要 license）
3. 點綠色 **「Create repository」** 按鈕

✅ 出現一個叫 "Quick setup" 的頁面，這就是空倉庫

---

## 步驟 3：上傳檔案 ⏱️ 3 分鐘

1. 在剛建好的空倉庫頁面，找到 **「uploading an existing file」** 連結點下去
   - 或直接到 `https://github.com/你的帳號/app-vault/upload/main`
2. 把這 5 個檔案**全部一起拖曳**到上傳區（或點選擇檔案後一次選全部）：
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
3. 等待全部上傳完成（每個檔旁邊會出現綠勾）
4. 滑到最下方：
   - **Commit message**：可填 "首次上傳" 或保留預設
   - 點綠色 **「Commit changes」** 按鈕

✅ 你會看到 5 個檔案出現在倉庫首頁

---

## 步驟 4：開啟 GitHub Pages ⏱️ 2 分鐘

1. 在倉庫頁面，點頂部 **「Settings」**（齒輪圖示）
2. 左側選單往下找 **「Pages」**
3. 在 **Build and deployment** 區塊：
   - **Source**：選 `Deploy from a branch`
   - **Branch**：選 `main` → `/ (root)` → 點 **Save**
4. 等 1–2 分鐘（GitHub 在後台建置）
5. 重新整理頁面，最上方會出現綠色框框，顯示你的網址：

```
✅ Your site is live at https://你的帳號.github.io/app-vault/
```

✅ 複製這個網址！這就是你的 App 網址了

---

## 步驟 5：在 iPhone 安裝到主畫面 ⏱️ 1 分鐘

1. iPhone 上**用 Safari** 打開你的網址（必須是 Safari，不能用 Chrome）
2. 確認頁面正常顯示
3. 點底部 **分享按鈕**（中間的方框 + 上箭頭）
4. 往下滑找 **「加入主畫面」** → 點下去
5. 確認名稱顯示 "App Vault" → 點右上角 **「加入」**

✅ 桌面就會出現紫色 9-grid 圖示的 App Vault 圖示

---

## 🎉 你現在擁有的東西

點桌面圖示就會：
- 開啟看起來像原生 App 的全螢幕介面（沒有 Safari 網址列）
- 資料用 localStorage 永久保存在 iPhone 上
- 可離線使用（service worker 已快取）
- App Store 真實 icon 全部正常顯示（沒有 sandbox 限制了）

---

## 💡 日常使用流程

**新增 App：**
1. 在 Claude 對話貼 App Store 網址 → Claude 給你 JSON
2. 打開 App Vault → 點「+ 新增」→ 貼上 JSON → 匯入

**備份資料：**
1. 點「匯出」→「下載 JSON 檔」→ 存到 iCloud
2. 換手機 / 重灌時，點「匯入備份檔」還原

**更新程式（未來如果想加新功能）：**
1. 回 GitHub 倉庫頁面
2. 點 `index.html` → 鉛筆圖示編輯，或重新上傳新版檔案
3. Commit 後約 1 分鐘自動更新到網站
4. 在 iPhone 上的 App 重新打開就會載入新版（資料不會丟）

---

## ❓ 常見問題

**Q：圖示沒出現在桌面？**
A：確認用 Safari 開（不能用 Chrome 加主畫面）

**Q：點圖示開啟還是有網址列？**
A：刪掉重加。或在 Safari 設定 → 進階 → 實驗功能，確認沒有關閉 PWA 相關選項

**Q：資料消失了？**
A：iOS 會在 7 天沒打開 PWA 時清掉 localStorage。建議每週用一次，或定期匯出備份

**Q：可以分享給別人用嗎？**
A：可以。網址是公開的，任何人都能打開使用。但每個人的資料是各自本地的

---

完成！有問題隨時回 Claude 對話問我 🚀
