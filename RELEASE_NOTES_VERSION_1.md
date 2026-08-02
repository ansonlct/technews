# VERSION 1 發布說明

發布日期：2026-08-02

## 正式版定位

VERSION 1 將先前開發版本整合為第一個正式穩定版，統一產品版本、PWA 快取、部署文件及資料輸出標示。

## 文章直連修正

- 修正空白網址被解析成 GitHub Pages 首頁。
- 空白、相對、非 HTTP/HTTPS、未驗證及 Google News wrapper 網址不可點擊。
- Google News signed-parameter 解碼改為每篇文章一個請求，避免批次回應錯位。
- 解碼後會核對新聞來源網域及可取得的原文標題。
- Redirect fallback 沒有相符標題時會被拒絕。
- 加入標題及來源級 `url_overrides.json` 修復機制。
- 舊資料遺失 Google wrapper 時，可按精確標題重新搜尋並再次驗證。
- 網頁、TXT 及 CSV 均不輸出未確認連結。
- 修正部分 RSS 把 `target="blank"` 等 HTML 屬性夾在文章網址後方的問題；收集、遷移及輸出均會清洗。

## 正式版強化

- 統一所有可見版本為 `VERSION 1`。
- PWA cache 升級為 `hk-risk-monitor-version-1`。
- Service Worker 不再以 `index.html` 回應失敗的 JavaScript、CSS 或圖片請求。
- 只有成功 HTTP 回應才會寫入 PWA cache；離線資料缺失會返回明確 503 JSON。
- 加入 Content Security Policy、no-referrer 及 PWA identity。
- `scripts/validate_web.py` 擴充為版本、JSON、CSV、HTML、PWA、圖示、網址、override 及 SQLite 完整檢查。
- 整理歷史發布文件至 `docs/history/`。
- seed database 已預先升級為 VERSION 1 完整 schema，並通過 SQLite integrity check。
- 移除正式套件內不應提交的 `runtime/news_monitor.db`，首次運行會由 seed 建立。
- 37 項單元測試及 6 項 subtests 全部通過。

## 已核實的指定文章

已核對並加入香港電台、am730、東網、香港經濟日報、橙新聞、明報、香港01、星島、信報、東方日報、文匯報及無綫新聞的指定原文網址。
