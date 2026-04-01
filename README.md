# jsonParser

純前端 JSON 解析工具，一個 HTML 檔案直接部署，零依賴，手機也能用。

## 功能

| 功能 | 說明 |
|------|------|
| 解析格式化 | 將 JSON 以縮排格式化輸出 |
| 壓縮一行 | 將 JSON 壓縮為單行（複製用） |
| 語法高亮 | key / string / number / boolean / null 五色標示 |
| 複製按鈕 | 成功解析後才出現，避免複製錯誤訊息 |
| 錯誤提示 | 常見錯誤自動提示（單引號、trailing comma 等） |
| 自動儲存 | 輸入內容存到 localStorage，重新打開還在 |
| 快速鍵 | Ctrl/⌘ + Enter 執行解析 |

## 部署

直接 `index.html`，無需建置工具：

```
# GitHub Pages
git push origin main
→ https://<your-user>.github.io/jsonParser
```

## 版本

目前版本：**v0.3.0**

## Changelog

| 版本 | 日期 | 異動 |
|------|------|------|
| v0.3.0 | 2026-04-01 | 修復 XSS（e.message 改用 esc() 跳脫）、移除無效 innerHTML+=''、localStorage 加 QuotaExceededError 保護、saveDraft debounce 改用外部 timer 變數、textarea 加 autocorrect/autocapitalize/spellcheck 屬性 |
| v0.2.0 | 2026-04-01 | 加語法高亮、壓縮按鈕、錯誤提示、localStorage、修復複製 bug |
| v0.1.0 | 2026-03-22 | 初始版本（格式化解折 + 複製 + Ctrl+Enter） |

## License

MIT
