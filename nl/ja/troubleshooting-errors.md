---

copyright:
  years: 2018
lastupdated: "2018-11-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# エラー・メッセージのトラブルシューティング
{: #error-message-troubleshooting}

このトピックでは、IBM© Cloud Load Balancer のインスタンスの作成時または更新時に出される可能性のある一般的なエラー・メッセージについて説明します。

| エラー | 説明  | 解決策  |
| ------------- | ------------- | ----- |
| ``ロード・バランサーの最大数 `n` に達しました (The maximum number of load balancers `n` has been reached.)。| 許可されるロード・バランサー・インスタンスの数は、アカウント当たり 50 のみです。 | アカウント当たりのロード・バランサー・インスタンスの数が 50 以下であることを確認してください。 |
| ``ロード・バランサー製品注文でのプロトコルの最大数 `n` に達しました (The maximum number of given protocols `n` in load balancer product order has been reached.)。 | ロード・バランサーのプロビジョン中に追加できるプロトコルは 2 つのみです。  | もっと多くのプロトコルが必要な場合、プロビジョンした後に、ロード・バランサー管理フローで**「プロトコル」**タブから最大 10 個まで追加できます。 詳しくは、[サービスのモニターと管理](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)を参照してください。 |
| ``ロード・バランサー製品注文でのサーバー・インスタンスの最大数 `n`に達しました (The maximum number of given server instances `n` in load balancer product order has been reached.)。 | ロード・バランサーのプロビジョン中に追加できるサーバーは 10 個のみです。 | 追加のサーバーが必要な場合、プロビジョンした後に、ロード・バランサー管理フローで**「サーバー・インスタンス」**タブから最大 50 個まで追加できます。 詳しくは、[サービスのモニターと管理](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-and-managing-your-service)を参照してください。 |
| ``ロード・バランサー名は 1 文字から 40 文字までの文字列でなければなりません (Load balancer name must be a string and have at least 1 and up to 40 characters)。 | ロード・バランサー名は必須です。 名前には英数字 (または特殊文字「-」および「.」) のみを使用してください。 名前の先頭と末尾の文字は特殊文字であってはならず、長さは 40 文字に制限されます。 | 固有のロード・バランサー名を入力してください。 例えば、「ui-servers」や「backend-servers」などです。|
| ``指定されたロード・バランサー名のフォーマットの誤りが見つかりました (Format error found in given load balancer name.)。 | ロード・バランサー名は必須です。 名前には英数字 (または特殊文字「-」および「.」) のみを使用してください。 名前の先頭と末尾の文字は特殊文字であってはならず、長さは 40 文字に制限されます。 | 固有のロード・バランサー名を入力してください。 例えば、「ui-servers」や「backend-servers」などです。|
| `同じ名前 (大/小文字を区別しない) のロード・バランサーが既に存在します (Load balancer with the same name (case insensitive) already exists.)。` | 同じ名前のロード・バランサーが存在します。 | 先に進むには、固有のロード・バランサー名を入力してください。例えば、「ui-servers」や「backend-servers」などです。 |
| `ロード・バランサー説明は、文字列でなければならず、255 文字を超えてはなりません。` | ロード・バランサーの説明は、255 文字を超えない文字列でなければなりません。| 説明を 255 文字に制限してください。|
| `フロントエンド・ポート 80 は既に使用されています (Frontend port 80 is already used.)。` | 既に使用中のフロントエンド・ポートを入力した可能性があります。| 固有のフロントエンド・ポートを入力してください。|
| `バックエンド・ポートは整数でなければなりません (Backend port must be an integer.)。` | 無効なバックエンド・ポート値を入力した可能性があります。 | 1 から 65535 までのバックエンド・ポート番号を入力してください。|
| `プロトコルおよびポートはヘルス・モニターでは編集できないため、UI からこのエラーには対処できません。`| プライベート・サブネットは標準タイプのものではないので、ロード・バランサーの作成に使用できません。| IBM サポートにお問い合わせください。|
| `プライベート・サブネット xyz には、少なくとも n 個の空き IP アドレスがなければなりません (Private subnet xyz must have at least n free IP addresses.)。`| 選択されたプライベート・サブネットには空き IP アドレスがありません。| 詳しくは、[トラブルシューティング手順](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-load-balancer-provisioning-troubleshooting)を確認してください。 |
| `指定されたプライベート・サブネット VLAN はルーター xyz 上にあります (Specified private subnet VLAN is on router xyz.)。しかし、同じルーター上では n 個の空き IP のあるパブリック VLAN は見つかりませんでした (However, no public VLAN with n free IPs was found on the same router.)。` | これが起こる原因は、プロビジョン中に**「このアカウントからパブリック・サブネットを割り振る (Allocate from public subnet from this accoount)」**オプションを選択したことです。 | 代わりに**「IBM システム・プールから割り振る (Allocate from IBM System Pool)」**を選択するか、または IBM サポートにお問い合わせください。|
| `指定されたプライベート・サブネット VLAN はルーター xyz 上にあります (Specified private subnet VLAN is on router xyz.)。しかし、同じルーター上では n 個の空き IP のあるサブネット VLAN は見つかりませんでした (However, no public subnet with n free IPs was found with VLAN on the same router.)。` | これが起こる原因は、プロビジョン中に**「このアカウントからパブリック・サブネットを割り振る (Allocate from public subnet from this accoount)」**オプションを選択したことです。 | 代わりに**「IBM システム・プールから割り振る (Allocate from IBM System Pool)」**を選択するか、または IBM サポートにお問い合わせください。|
| `指定する新規説明は文字列でなければなりません (Given new description must be a string.)。`| 無効な説明を入力した可能性があります。 | 255 文字を超えない有効なロード・バランサー説明を入力してください。|
| `ロード・バランサー uuid=aaaa-bbbb-cccc-dddd の取り消しを処理するための請求項目が必要です (A billing item is required to process a cancellation for load balancer uuid=aaaa-bbbb-cccc-dddd.)。` | アカウントの請求先情報が欠落しているか無効です。ロード・バランサーをキャンセルできませんでした。| IBM サポートにお問い合わせください。|
| `内部エラーが発生しました (An internal error occurred.)。 データを取得できませんでした (Data could not be retrieved.)。` | メトリック・データを取得できません。 | ページを再ロードします。それでも問題が解決しない場合は、IBM サポートにお問い合わせください。|
| `フロントエンド・ポートは、56500 から 56520 までの範囲を除く、1 から 65535 までの整数でなければなりません (Front-end port must be an integer between 1 and 65535 excluding the range 56500-56520.)。` | 56500 から 56520 までのフロントエンド・ポート番号を入力した可能性があります。| 1 から 65535 までの固有のポート番号 (ただし 56500 から 56520 の範囲は除く) を入力してください。|
| `バックエンド・ポートは整数でなければなりません (Back-end port must be an integer.)。` | 無効なバックエンド・ポート値を入力した可能性があります。 | 1 から 65535 までのバックエンド・ポート番号を入力してください。|
| `バックエンド・ポートは、56500 から 56520 までの範囲を除く、1 から 65535 までの整数でなければなりません (Back-end port must be an integer between 1 and 65535 excluding the range 56500-56520.)。` | 56500 から 56520 までのバックエンド・ポートを入力した可能性があります。| 1 から 65535 までのバックエンド・ポート番号 (ただし 56500 から 56520 の範囲は除く) を入力してください。|
| `バックエンド・プロトコル HTTP はフロントエンド・プロトコル TCP と互換ではありません (Backend protocol HTTP is not compatible with frontend protocol TCP.)。` | 互換ではないバックエンド・プロトコルとフロントエンド・プロトコルの組み合わせを選択した可能性があります。 | 次の形式で、有効なフロントエンドとバックエンドのプロトコルの組み合わせを入力します。`<br> HTTP-HTTP <br> HTTPS-HTTP <br> TCP-TCP` |
| `メンバー重み <some value> がメンバー abcd-xxxx-yyyy-2222 に対して指定されています (Member weight <some value> is provided for member abcd-xxxx-yyyy-2222.)。 許可される重み値は 0 から 100 までです (The allowed weight value is 0-100.)。 `| 無効な重みを入力した可能性があります。 | 0 から 100 までの重みの値を入力します。|
| `サーバーの取り出し中に問題が発生しました (There was a problem fetching the servers.)。` | これはネットワーク・タイムアウトの問題の結果として生じることがあります。| ページを再ロードします。それでも問題が解決しない場合は、IBM サポートにお問い合わせください。|
