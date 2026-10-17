# 讓 AI Agent、MCP Server、CLI 安全登入的實作工作坊

> Hello World Dev Conference 2026

## 活動資訊

| 項目     | 內容                                                                    |
| -------- | ----------------------------------------------------------------------- |
| 活動     | [Hello World Dev Conference 2026](https://2026.helloworld.dev/)         |
| 日期     | 2026-10-14                                                              |
| 時間     | 13:30 – 15:00                                                           |
| 地點     | 臺北文創大樓 6 樓                                                       |
| 形式     | 90 分鐘 Workshop（實機操作）                                            |
| 語言     | 中文                                                                    |
| 徵稿主題 | 徵稿主題 4｜AI 驅動的軟體開發資安新思維                                 |
| Repo     | <https://github.com/go-training/mcp-oauth2-workshop>                    |
| 投影片   | [workshop-zh.html](./workshop-zh.html)                                  |

## 講者

**吳柏毅（appleboy）**
聯發科技 後端架構工程師

## 議程簡介

MCP 授權規格的方向是**把 MCP Server 視為 OAuth 的 Resource Server**。學員從一支沒有任何認證、誰都能呼叫的 MCP Server 出發，一關一關補上正確的授權層，並使用現場已架好的認證閘道 Signet，重心全放在自己筆電上的 MCP Server 與 Client。

## 課程路線

| Lab    | 時間     | 問題                       | 重點                                                     |
| ------ | -------- | -------------------------- | -------------------------------------------------------- |
| Lab 01 | 10 分    | 沒有授權會怎樣？           | 任何人都能呼叫所有工具                                   |
| Lab 02 | 15 分    | Client 怎麼知道去哪登入？  | 401 → PRM（RFC 9728）→ AS metadata（RFC 8414）           |
| Lab 03 | 25 分    | 怎麼證明你是誰？           | Authorization Code + PKCE（RFC 7636），Server 驗 JWT     |
| Lab 04 | 20 分    | 你能做什麼、能去哪？       | scope、audience（RFC 8707）、subject 隔離                |
| Lab 06 | 10 分    | 多個服務怎麼共用入口？     | Kong + mcp-oauth2 plugin 集中驗 Token                    |
| Lab 05 | 課後選修 | 撤銷後會立刻失效嗎？       | 離線驗證的限制                                           |

## 帶走這七件事

1. 401 + PRM 告訴 Client 去哪登入；Server 不代替 Client 登入
2. public Client 沒有 secret，靠 PKCE 保護授權碼
3. 每次呼叫 MCP 都要帶 Access Token
4. Server 驗簽章、iss、aud、exp、type
5. 401 是 Token 不被接受；403 是權限不夠
6. Gateway 集中入口驗證，工具與資料權限仍留在服務
7. 撤銷不等於立即失效，離線驗證要另外處理

## 前置需求

- 可執行 Docker / Docker Compose 的筆電（macOS、Linux 或 Windows WSL2）
- 已安裝 `git`、`curl`、`jq` 與任一終端機
- 事先拉取工作坊映像檔
- 基本 HTTP 與終端機操作能力；不需事先熟悉 OAuth 或 MCP

## 參考資料

- MCP Authorization 規範：<https://modelcontextprotocol.io/specification/2026-07-28/basic/authorization>
- Kong mcp-oauth2 plugin：<https://github.com/go-signet/kong-mcp-oauth2>

## 標籤

`MCP` `OAuth 2.0` `PKCE` `RFC 9728` `Kong`
