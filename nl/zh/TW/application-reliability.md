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

# 使用來自 IBM Cloud Internet Services 的「廣域負載平衡」來改善應用程式可靠性及可調整性
如果您有電子商務網站，或是管理的應用程式需要讓一般使用者隨時都能存取，則您可能會關心應用程式的 24*7 可用性及效能。 

IBM Cloud Internet Services (CIS) 提供的廣域負載平衡功能可協助改善應用程式的可靠性及可調整性，同時提供可能最好的一般使用者體驗。本手冊提供廣域負載平衡配置的逐步演練。  

## 您將達成的目標

在此「逐步」中，您將學習如何配置與下列圖解類似的配置。

<img src="images/Reliability1.png" alt="圖片" style="width: 300px;"/>

在此範例中，應用程式資源會部署在兩個資料中心位置中，一個在美國西部，另一個在美國東岸。一般使用者可能正在從世界各處存取此應用程式。 

作業  |說明 
------------- | -------------
[建立 CIS 實例](create-cis.html) | 使用「IBM 客戶入口網站」開始建立 IBM Cloud Internet Services (CIS) 實例。
[輸入網域的相關資訊](input-domain.html) | 輸入您要保護，並為其提供廣域負載平衡之網域的相關資訊。
[開始廣域負載平衡器配置](begin-config.html) | 開始配置「廣域負載平衡器」。
[識別應用程式資源](identify-app-resources.html) | 識別應用程式的資源，例如原始儲存區及性能檢查機制。
[定義廣域負載平衡器](define-global-lb.html) | 定義廣域負載平衡器配置，方法為指定主機名稱、新增並調整原始儲存區，以及定義其他規則來控制如何將資料流量提供給用戶端。
