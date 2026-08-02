# 升級至 VERSION 1

1. 備份目前 repository。
2. 用 VERSION 1 套件內的檔案覆蓋 repository 根目錄。
3. 必須包括 `.github/`、`src/`、`scripts/`、`tests/`、`web/`、`url_overrides.json` 及 `seed/news_monitor_seed.db`。
4. 舊的 `seed/news_monitor_v1.4.1.db` 可刪除。
5. 不要上傳 `runtime/news_monitor.db`；GitHub Actions Cache 會保留運行資料，沒有 cache 時會由 seed 自動建立。
6. Commit／push 到 `main`。
7. 到 Actions 手動執行一次 **Update news and deploy website**。
8. 完成後重新載入網站；已安裝 PWA 會自動移除舊 cache。

升級不會要求 API Key。舊資料庫 schema 會自動遷移，已核實的 curated URL 不會被 Google News resolver 覆蓋。
