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

# アプリケーション・リソースの識別

起点プールやヘルス・チェック・メカニズムなど、アプリケーションのリソースを識別します。
 
1. **「起点プール (Origin Pools)」**セクションにナビゲートし、**「プールの作成 (Create pool)」**をクリックして新規起点プールを定義します。 

   起点プールは、アプリケーションをお客様に配信するサーバー・リソースです。 
   
2. 起点プールに名前を割り当て、以前に定義したヘルス・チェック・メカニズムを選択します。アプリケーション・サーバーを起点として追加します。**「オリジンの追加 (Add Origin)」**をクリックすると、1 つ以上の起点を追加できます。 

   **注:** IBM Cloud Load Balancer などのローカル・ロード・バランサーの後ろにアプリケーション・サーバーが配置されている場合は、個々のサーバーを追加するのではなく、ロード・バランサーの FQDN または仮想 IP を起点として追加してください。 
   
3. **「リソースのプロビジョン (Provision Resource)」**をクリックし、起点プールの作成を完了します。  

   <img src="images/Reliability6.png" alt="図" style="width: 300px;"/>
   
   起点プールは最初は**「正常でない (Unhealthy)」**として表示されます。この状態は、システムがヘルス・チェックを問題なく完了した後、**「正常 (Healthy)」**に変わります。状態の変化を確認するには、ブラウザーを最新表示する必要がある場合があります。 
   
   <img src="images/Reliability9.png" alt="図" style="width: 300px;"/>
   
   **注:** 起点プール内に複数の起点がある場合、正常な起点のしきい値を使用して、プールの正常性を宣言する前に正常な状態になくてはならない起点の最小数を指定します。 
   
4. 存在するアプリケーション・ファームの数と同数の起点プールを定義します。これらのファームは同じ地域にあっても、異なる地域にあってもかまいません。この例では、米国の西海岸と東海岸にあるアプリケーション・ファームを示す 2 つの起点プールを作成します。 

   <img src="images/Reliability10.png" alt="図" style="width: 300px;"/>