# 泥研製所：猜猜我是誰

官網外嵌小遊戲。認識六位材料夥伴，全部答對（錯一題就沒有）揭曉小禮物（留下 Email 領 95 折優惠碼），並引導加入會員。

## 檔案

| 路徑 | 用途 |
|---|---|
| `public/index.html` | 遊戲本體（材料資料、答對門檻 `PASS` 都在檔案裡的設定區） |
| `public/cat.svg` | 胖胖貓 |
| `functions/api/claim.js` | 收 Email、存進 D1、回傳優惠碼 |
| `wrangler.toml` | Pages 設定：D1 綁定（DB → game）、優惠碼 `COUPON_CODE` |
| `官網嵌入碼.html` | 貼到 SHOPLINE「自訂 HTML」（框框高度跟著遊戲內容變，不出現捲軸；需要搭配新版外嵌碼） |

## 部署

推到 GitHub `main` 分支，Cloudflare Pages 會自動部署。

- 換優惠碼：改 `wrangler.toml` 的 `COUPON_CODE`，推上去
- 改答對門檻：`public/index.html` 和 `functions/api/claim.js` 的 `PASS` 要一起改
- 名單和其他小遊戲共用 D1 的 `game_leads` 表，從 niyan_Game 的 `/api/leads?key=管理密碼` 下載，遊戲欄會顯示「猜猜我是誰」

## 本機測試

```
wrangler pages dev
```
