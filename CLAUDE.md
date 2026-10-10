# 健身記帳 App

## 網址與部署
- **正式網址**：https://sunnymath17play.github.io/gym/
- 用 GitHub Pages 發布：PR 合併進 `main` 後，約 1～3 分鐘自動更新，**不需要手動上傳**。
- **舊網址已停用**：winsungym.netlify.app（Netlify）。不要再用，也不要去 Netlify 找這個 App。第一筆 commit 訊息提到 Netlify，那是搬家前的舊版。

## 檔案
- `index.html`：整個 App（React + Babel，從 CDN 載入，沒有建置步驟）
- `manifest.json`、`icon-*.png`：主畫面圖示與全螢幕設定

## 登入與資料
- Google 登入＋Firebase 專案 `winnie-bloodsugar`，資料存在 Firestore 集合 `gym`（文件 `state`）。
- **誰能登入**由 Firestore 規則裡的 email 名單決定，規則不在這個 repo 裡。要改名單得到 Firebase 主控台 → Firestore → 規則：
  https://console.firebase.google.com/project/winnie-bloodsugar/firestore/databases/-default-/rules
- 目前名單：sunnymath30@gmail.com（SUNNY）、swear.coco@gmail.com（Winnie）。
- 登入 Firebase 主控台要用有專案權限的帳號（瀏覽器右上角是黃色太陽頭像的那個），而且帳號要開兩步驟驗證。
- App 左上角會顯示目前登入的帳號，旁邊有「登出」，可以換帳號。

## 待處理
- 同一個 Firebase 專案的 `readings` 集合（血糖 App）規則是 `if true`，任何人都能讀寫，還沒鎖起來。

## 協助 SUNNY 時
- 先查清楚再給步驟：讀這份文件和 `git log`，必要時翻之前的對話。確認網址、部署方式、帳號之後才開始教，不要用猜的。
- 用繁體中文，一步一步教。
