# 🐱 習慣小貓 · Habit Cat (v3)

> 療癒系習慣養成網頁遊戲，畫面高度還原《旅行青蛙》，支援 Gmail 登入與雲端同步。

## 新功能

1. **Gmail / Google 登入**
2. **資料存到帳號**（Firestore 雲端同步）
3. **成就系統** — 預設 10/50/100/300/500/1000 次，也可自訂成就

## 線上玩

**https://sumovt.github.io/habit-cat-new/**

## 啟用雲端登入（必做）

1. 到 [Firebase Console](https://console.firebase.google.com) 建立專案
2. Authentication → 啟用 Google 登入
3. Firestore → 建立資料庫（測試模式即可）
4. 專案設定 → 新增 Web 應用 → 複製 `firebaseConfig`
5. 打開 `index.html`，搜尋 `YOUR_API_KEY`，把整段 `firebaseConfig` 換成你複製的內容
6. 存檔並重新部署

建議 Firestore 規則：
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## License
MIT
