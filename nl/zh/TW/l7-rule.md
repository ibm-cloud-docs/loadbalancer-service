---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 第 7 層規則
{: #layer-7-rules}

第 7 層規則定義要與特定值比對的送入資料流量部分。

* 如果送入的資料流量符合指定的規則值，則規則會評估為 `true`。
* 第 7 層規則一律與第 7 層原則相關聯。多個第 7 層規則可以與相同的第 7 層原則相關聯。
* 如果多個規則與某個原則相關聯，則每個規則都會評估為 `true` 或 `false`。 
* 如果與原則相關聯的所有規則都評估為 `true`，則會將原則動作套用至該要求。否則，負載平衡器會評估下一個原則。

規則的類型可以是： 

* `HOST_NAME`
* `FILE_TYPE`
* `HEADER`
* `COOKIE`
* `PATH`

這些指出要與規則比對的第 7 層資料流量部分。

類型      | 要擷取及評估的欄位
----------| -----------------------
`HOST_NAME` |URL 的主機名稱部分（例如 `api.my_company.com`）
`FILE_TYPE` |URL 的結尾，代表檔案類型（例如 `jpg`）
HEADER    | HTTP 標頭中的欄位
COOKIE    | HTTP 標頭中的具名 Cookie
PATH      |主機名稱後面的 URL 部分（例如 `/index.html`）

規則也具有比較類型，可指出其評估方式。規則可具有下列比較類型： 

* `REGEX`
* `STARTS_WITH`
* `ENDS_WITH`
* `CONTAINS`
* `EQUAL_TO`

比較類型        |  評估類型
----------------|---------------------
`REGEX`           |比對擷取的欄位（例如 `hostname`）與提供的正規表示式
`STARTS_WITH`     |  驗證擷取的欄位是否以提供的字串為開頭
`ENDS_WITH`       |  驗證擷取的欄位是否以提供的字串為結尾
`CONTAINS`        |  驗證擷取的欄位是否包含提供的字串
`EQUAL_TO`        |  驗證擷取的欄位是否與提供的字串相同

**附註**：並非所有規則類型都支援所有比較類型。例如，如果您使用 `FILE_TYPE`，則最好使用比較類型 `REGEX` 及 `ENDS_WITH`。

## 第 7 層規則內容

內容      |說明 
------------- | -------------
類型 | 指定規則的類型。規則類型可以是 `HOST_NAME`（主機名稱）、`FILE_TYPE`（檔案類型）、`HEADER`（標頭）、`COOKIE`（Cookie）或 `PATH`（路徑）。
比較類型        | 比較類型用於與規則類型、索引鍵及值相關聯，以定義規則及分類資料流量。比較類型可以是：`REGEX`、`STARTS_WITH`、`ENDS_WITH`、`CONTAINS` 及 `EQUAL_TO`。
索引鍵 | 規則類型 `HEADER` 及 `COOKIE` 的說明索引鍵。
值 | 對於規則類型 `HEADER` 及 `COOKIE`，值會與索引鍵進行比較。
反轉 | 如果您將值設為 1，則只要指定的規則不相符時，就會將此 L7 規則比較的值設為 `true`。
第 7 層原則 ID | 附加規則之原則的唯一 ID。
