# CLAUDE.md — jsonParser

## 專案概述
純前端單檔 JSON 工具（index.html），零依賴，無需建置。直接開啟 HTML 即可使用，也可部署到 GitHub Pages。

## 開發原則
- **維持單一 HTML 檔案**，不引入任何外部依賴（無 npm、無 CDN）
- 語法高亮用 regex replace + innerHTML，所有使用者可見字串都必須先過 `esc()`
- 版本號需同步更新四處：`<title>`、`<meta name="version">`、badge `<span>`、`README.md` Changelog

## 安全規則
- `showError()` 中錯誤訊息必須用 `esc()` 做 HTML 跳脫，防止 XSS
- `highlightJSON()` 的 regex match 結果已透過 `esc()` 跳脫，維持此做法

## 已知風險與對策
| 風險 | 對策 |
|------|------|
| XSS via e.message | showError 中用 esc() 包裹 |
| localStorage QuotaExceededError | saveDraft 包在 try/catch 內靜默忽略 |
| 手機自動修正 JSON | textarea 加 autocorrect="off" autocapitalize="off" spellcheck="false" |
| debounce timer 污染 function 物件 | 使用外部 let saveDraftTimer 變數 |

## 不要做的事
- 不要在 showError 裡直接 `result.innerHTML = '...' + e.message`（XSS）
- 不要用 `saveDraft._t` 把 timer 掛在 function 上（反模式）
- 不要在 showError 結尾加 `result.innerHTML += ''`（無意義且觸發 DOM 重繪）
