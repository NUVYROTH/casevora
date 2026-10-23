# Casevora 食品客訴分析助手

## 兩個版本，每次修改都要一起更新

| 版本 | 位置 | 說明 |
|---|---|---|
| 網址版 | GitHub 倉庫 `NUVYROTH/casevora` 的 `main` → https://nuvyroth.github.io/casevora/ | 公開，沒有 AI 分析 |
| claude.ai 版 | https://claude.ai/artifact/CcVVJNTc9SaktSAPAj6nqb | 私人（擁有者分享才看得到），有 AI 分析 |

- 原始檔只有一份：`index.html`。
- **每次修改都要兩邊一起更新。claude.ai 版一律用上面同一個網址更新（Artifact 工具帶 `url`），不要建立新的 artifact。**
- 更新 claude.ai 版的步驟：
  1. `python3 tools/build_claude_html.py <暫存資料夾>/casevora-claude.html`
  2. 用 Artifact 工具發布該檔案，`url` 填上面的 claude.ai 版網址。
  3. capabilities 維持 `{"sample": {"images": true}, "downloads": true}`。**不要宣告 `db`**（不使用共用資料庫，資料只存在各自瀏覽器）。

## 修改流程

1. 先開 `preview-xxx` 分支修改並推上去（GitHub Pages 只發布 `main`，所以不影響網站）。
2. 用假資料測試（例：消費者 A、王小明 0912-345-678、TEST-001），電腦與手機尺寸都測。
3. 擁有者確認「可以上線」後才合併到 `main`，並同步更新 claude.ai 版。

## 不能改變的原則

- 程式碼裡不能有任何金鑰（API key、`service_role` 等）。
- AI 分析用「使用者自己的 Claude 帳號」（`claude.use('sample')`），不串 API 金鑰。
- AI 分析建議只顯示在右欄，**不儲存**到案件；案件只保存左欄由人填寫的內容。
- 不判定責任歸屬；「權責單位」是負責改善的部門，不是犯錯的人。
- 頁面上的誠實文案（本機儲存、僅在此裝置此瀏覽器有效）不能拿掉。
- 刪除欄位時，舊案件的資料要保留在資料中，不可直接清除。
