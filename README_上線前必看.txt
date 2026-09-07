欠款記帳 v1.03｜登入安全修正版

1. 先到 Firebase Console：
   Authentication → Sign-in method → Email/Password → Enable
   Google 登入保持啟用。

2. 再把這份 index.html 覆蓋 GitHub money 專案目前的 index.html。

3. 舊帳號第一次更新後：
   - 優先使用 Google 登入。
   - 若舊資料庫仍有舊密碼，系統會嘗試搬到 Firebase Authentication。
   - 搬移成功後，會刪除舊的 user_credentials 密碼資料與 bindings/customPass。
   - 若找不到可搬移的舊密碼，系統會要求已通過 Google 驗證的本人設定一組新密碼。

4. 新版之後：
   - 新密碼不再寫入 Realtime Database。
   - 自訂帳密由 Firebase Authentication 驗證。
   - localStorage 的 app_auth 不再能偽造登入。

5. 重要：
   舊版曾暴露在前端原始碼中的管理員密碼應視為已外洩，請不要繼續沿用；
   更新後用 Google 登入並設定新密碼。

6. 此次主要修正「自訂帳密 / 密碼安全」。
   Firebase Realtime Database Rules 仍應另外檢查，才能完整限制資料與管理權限。
