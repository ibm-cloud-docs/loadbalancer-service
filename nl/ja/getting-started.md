---

copyright:
  years: 2017, 2018
lastupdated: "2019-04-29"

keywords: load balancer, order, ibmid

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}


# IBM Cloud Load Balancer の使用開始
{: #getting-started}

IBM© Cloud Load Balancer の使用を開始するには、主に次の 2 つの項目が必要です。

* IBM のアカウント: [IBMid ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/account/us-en/signup/register.html){:new_window}
* IBM サーバー ([ベア・メタル](/docs/bare-metal?topic=bare-metal-about)または[仮想サーバー・インスタンス (VSI)](/docs/vsi-is?topic=virtual-servers-is-gettingstartedvsigen#gettingstartedvsigen))

**IBMid** アカウントの取得について支援が必要な場合は、[IBM 営業担当員 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/contact-us){:new_window} にお問い合わせください。

既存の IBM Cloud Infrastructure (SoftLayer) アカウントをお持ちの場合は、IBMid と[アカウントをリンク](/docs/account?topic=account-unifyingaccounts)できます。

## ロード・バランサーを注文する
{: #ordering-a-load-balancer}

IBM Cloud Load Balancer サービスを注文するには、[IBM Cloud カタログ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")]( https://cloud.ibm.com/catalog/infrastructure/load-balancer-group){:new_window} から**「IBM Cloud Load Balancer」**を選択します。次に、**「作成」**をクリックして、以下の手順を実行します。

1. 名前および説明など、基本的なサービス・パラメーターを定義します。
2. データ・センターを選択します。
3. ロード・バランサーのタイプとして**「パブリック」**を選択します。
4. ロード・バランサーをデプロイするサブネットを選択します。

  ロード・バランサー・サービス・インスタンスは、このサブネット上にいずれかのネットワーク・インターフェースを持ちます。 アプリケーション・サーバーがこのサブネット上にあるか、またはこのサブネットから到達できることを確認してください。 必要な場合は、VLAN スパンニングを有効にします。
  {: note}

5. フロントエンドとバックエンドのアプリケーション・プロトコルおよびポートを作成します。

  この構成について詳しくは、[IBM Cloud ロード・バランサーのパラメーターの構成](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configuring-ibm-cloud-load-balancer-parameters)を参照してください。
  {: note}

6. SSL オフロードを有効にするには、フロントエンド・プロトコルを HTTPS に設定し、バックエンド・プロトコルを HTTP に設定します。それから、「証明書」ドロップダウン・ボックスから「SSL 証明書」を選択します。

  既存のすべての SSL 証明書は、[IBM Cloud 証明書ストア ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/classic/security/sslcerts){:new_window} を介して管理されます。SSL 証明書がない場合は、ここで作成できます。

7. 必要な場合は、ヘルス・チェック・パラメーターを調整してください。そうでない場合、デフォルト設定を使用します。

  ヘルス・チェック・パラメーターについて詳しくは、[IBM Cloud ロード・バランサーのパラメーターの構成](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-configuring-ibm-cloud-load-balancer-parameters#configure-health-checks)を参照してください。
  {: note}

8. **「サーバーの関連付け (Attach Server)」**をクリックして、ロード・バランサーの後ろにある 1 つ以上のサーバー・インスタンスを関連付けます。表示されるサーバー・インスタンスは、ご使用のデータ・センターからローカルとなるサーバー・インスタンスのみです。
9. ページを確認し、サービスのご使用条件を確認してから、**「作成」**をクリックします。

ロード・バランサーのリストが表示され、すべてのサービス・インスタンスが表示されます。

このページにあるサービス名をクリックすると、そのサービスの概要ページが表示されます。 **「プロトコル」**タブ、**「ヘルス・チェック」**タブ、および**「サーバー・インスタンス」**タブにナビゲートして、構成をさらに編集することができます。

新しく作成したロード・バランサーは、このリストにすぐに表示されない場合があります。数分後、新しいロード・バランサーはグレイで表示され、そのステータスは `Offline` になります。さらに数分後、新しいロード・バランサーは緑色で表示され、ステータスが `Online` になっていることが示されます。画面を最新表示しないと、これらの変更が表示されない場合があります。
{: note}

新しい Cloud Load Balancer のステップバイステップの構成手順については、[柔軟なサーバー・ロード・バランシングのための IBM Cloud Load Balancer の使用法](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-creating-and-using-an-ibm-cloud-load-balancer-for-elastic-server-load-balancing)を参照してください。
