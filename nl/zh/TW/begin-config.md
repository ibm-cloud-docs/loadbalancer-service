---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 開始廣域負載平衡器配置
開始配置「廣域負載平衡器」。

1. 在**可靠性**區段下，選取**廣域負載平衡器**。 
    
    <img src="images/Reliability6.png" alt="圖片" style="width: 300px;"/>

2. 向下捲動至「性能檢查」區段。 

   **附註：**此為選用配置。如果您未定義任何自訂性能檢查，則系統將使用 "/" 作為預設性能檢查路徑。 

3. 按一下**建立性能檢查**按鈕來定義一個自訂性能檢查。   

   提供您要在其上處理性能檢查的路徑。您可能使用 HTTP 或 HTTPS 通訊協定，進行性能檢查。 
   
4. 在**進階選項**下，您可以自訂其他參數，例如「進階」選項下的性能檢查間隔、重試次數、要求方法、回應方法，以及回應內文。 
   
   <img src="images/Reliability6.png" alt="圖片" style="width: 300px;"/>
   
5. 按一下**佈建資源**來完成性能檢查配置。 
