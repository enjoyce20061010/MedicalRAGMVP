# 系統架構

[返回目錄](../README.md)

## 功能分層

![流程圖 1](../assets/diagrams/02-architecture-1.png)

[放大查看](../assets/diagrams/02-architecture-1.png) · [圖表原稿](../diagram-sources/02-architecture-1.mmd)

此圖為功能分工示意；表單與 API 是不同入口。

## 服務呼叫關係

![流程圖 2](../assets/diagrams/02-architecture-2.png)

[放大查看](../assets/diagrams/02-architecture-2.png) · [圖表原稿](../diagram-sources/02-architecture-2.mmd)

實體部署涉及 Windows、WSL 與 Docker。此對外說明以服務關係呈現，環境位址及連接埠由部署文件另行管理。

| 元件 | 職責 |
|---|---|
| Portal／獨立網頁 | 接收操作、呈現結果 |
| Nginx | 網頁服務與請求轉發 |
| FastAPI | 認證、請求整理、追蹤與回應格式化 |
| n8n | 編排解析、資料查詢、檢索與模型呼叫 |
| 語言模型 | 問題處理與回答生成 |
| Embedding | 將文字轉為檢索向量 |
| Supabase／PostgreSQL | 資料與向量儲存，以及相關流程資料管理 |

## 交付資料實際畫面

以下為 2026-02-08 交付紀錄所附的原始截圖，用於對照介面與工作流。畫面保留當時版本，並非本次重新操作或執行結果；配置細節可能與概念流程圖不同。

### 統一後端 API 文件

![統一後端 API 文件](../assets/screenshots/api-swagger.png)

Swagger 畫面列出健康檢查、AI 問答與 JSON 上傳接口，對應架構中的 FastAPI 服務層。

[放大查看](../assets/screenshots/api-swagger.png) · 原始檔：`1.3_swagger_ui.png`

### 健康紀錄查詢工作流

![健康紀錄查詢工作流](../assets/screenshots/workflow-health.png)

交付時的 Health Record Controlled Pipeline 畫布，呈現查詢、檢索及模型處理相關節點；為歷史配置畫面。

[放大查看](../assets/screenshots/workflow-health.png) · 原始檔：`4.5_Health_Record_Pipeline_workflow.png`

