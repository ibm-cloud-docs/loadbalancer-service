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

# ドメインに関する情報の入力
保護してグローバル・ロード・バランシングを提供する対象のドメインに関する情報を入力します。

1. 「開始」画面の左側の**「概要」**をクリックします。 ドメイン・ネーム (またはサブドメイン・ネーム) を入力して**「ドメインの追加」**をクリックします。 
    
    <img src="images/Reliability3.png" alt="図" style="width: 300px;"/>
    
    **注:** IBM Cloud Internet Service は DNS 登録機関ではないため、このドメイン (またはサブドメイン) を事前に作成しておく必要があります。

    「サービス詳細 (Service Details)」セクションの下に、新規追加されたドメインが最初は「処理待ち」の状態で表示されます。 

    <img src="images/Reliability4.png" alt="図" style="width: 300px;"/>    

2. 各 DNS 登録者でドメインの管理ページへナビゲートし、NS レコードを定義することでドメイン/サブドメインを IBM ネーム・サーバーに代理委任します。

情報が DNS データベース内に複製されるまで、最大 24 時間待たなければならない場合があります。 完了すると、ドメインの状態が「アクティブ」に変わります。 

<img src="images/Reliability5.png" alt="図" style="width: 300px;"/>    
