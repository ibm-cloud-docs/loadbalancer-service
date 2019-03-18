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

# 輸入網域的相關資訊
針對您要保護並為其提供廣域負載平衡的網域，輸入相關資訊。

1. 按一下「開始使用」畫面左側的**概觀**。輸入「網域名稱」（或「子網域名稱」），然後按一下**新增網域**。 
    
    <img src="images/Reliability3.png" alt="圖片" style="width: 300px;"/>
    
    **附註：**IBM Cloud Internet Services 不是 DNS 登記員，所以先前必須已建立此網域（或子網域）。

    在「服務詳細資料」區段下，您將注意到剛新增的網域起始是以「擱置」狀態顯示。 

    <img src="images/Reliability4.png" alt="圖片" style="width: 300px;"/>    

2. 使用各自的 DNS 登記員來導覽至網域的管理頁面，並藉由定義 NS 記錄，將網域/子網域委派給 IBM 名稱伺服器。

在 DNS 資料庫中抄寫您的資訊，您最長可能必須等待 24 小時。一旦完成，您的網域狀態將變更為作用中。 

<img src="images/Reliability5.png" alt="圖片" style="width: 300px;"/>    
