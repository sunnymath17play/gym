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
- **iPhone 主畫面圖示裡不能 Google 登入**：`signInWithPopup` 在主畫面 App 裡會卡在 `winnie-bloodsugar.firebaseapp.com` 的白畫面（Unable to save initial state… sessionStorage is inaccessible），而且主畫面 App 拿不到 Safari 的登入（已實測：Safari 登入後刪掉再加回熊熊，仍是登出狀態）。
- 所以主畫面 App（`navigator.standalone`）改用 **email＋密碼**登入：先在 Safari 用 Google 登入，點左上角「設定密碼」（`linkWithCredential` 把密碼加到同一個帳號，`email_verified` 仍為 true，規則不用改），之後在熊熊裡用 email＋密碼登入。需要 Firebase 主控台 → Authentication → 登入方式 → 開啟「電子郵件/密碼」。

## 待處理
- 同一個 Firebase 專案的 `readings` 集合（血糖 App）規則是 `if true`，任何人都能讀寫，還沒鎖起來。

## 協助 SUNNY 時
- 先查清楚再給步驟：讀這份文件和 `git log`，必要時翻之前的對話。確認網址、部署方式、帳號之後才開始教，不要用猜的。
- 用繁體中文，一步一步教。
