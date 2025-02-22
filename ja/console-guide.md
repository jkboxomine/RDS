## Database > RDS for MySQL > コンソール使用ガイド

## 開始する

RDS for MysQLを使用するには、先にDBインスタンスを作成する必要があります。DBインスタンスは次の方法で作成できます。

* **Console > Database > RDS for MySQL**の **DB Instance **タブで左上の **+ 作成** ボタンをクリックすると、下図のようにページの下に入力画面が現れます。

![rds_01_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_01_20210112_jp.png)

* **詳細設定** 画面に表示された必須項目をすべて入力した後、画面右上の **次へ** ボタンをクリックします。
    * DB Instance：DBインスタンス名を入力します。
    * 説明：DBインスタンスの説明を入力します。
    * DB Engine：作成するデータベースエンジンバージョンを選択します。
    * DB Port：データベースのポート番号を入力します。 
        * 10000～12000の間で設定できます。
    * DB User ID：データベース作成時に作成される管理者アカウントIDを入力します。
    * DB Password：データベース作成時に作成される管理者アカウントパスワードを入力します。
    * VPC Subnet：作成するDBインスタンスとprivate network通信をするCompute & Networkサービスのサブネットを選択します。
    * Floating IP：NHN Cloudクラウド外部ネットワークと接続する場合、Floating IPを使用に設定します。
    * Flavor：DBインスタンスのタイプを選択します。
    * Storageタイプ：DBインスタンスボリュームのタイプを指定します。
        * HDDおよびSSDを選択できます。
    * Storage：DBインスタンスボリュームのサイズを入力します。 
        * 20GB～2TBのサイズで作成できます。
    * Availabillity Zone：DBインスタンスが作成される領域を選択します。
    * 高可用性：DBインスタンスを作成する時、Masterとは異なるAvailability ZoneにCandidate Masterを作成します。
    * Ping Interval：高可用性使用時、 Masterインスタンスの状態を確認する時間間隔を設定します。4回失敗すると障害と判断します。
        * 1～600秒の間で設定できます。
    * DBファイルの暗号化：ユーザーデータファイルおよびバックアップファイルを暗号化します。
    * 基本アラーム：DBインスタンスのイベントのうち、定義されているイベントに対するアラームを登録できます。
        * 基本アラーム使用時、受信グループを選択する必要があります。

> [参考]選択したComputeおよびNetworkのサービスのVPCサブネットがインターネットゲートウェイと接続されていない場合、Floating IPを使用できません。
> [参考]一度選択したVPCサブネットは変更できません。
> [参考] Candidate Masterインスタンスは、必ずMasterと異なるAvailability Zoneに作成され、リストに表示されません。
> [参考]インスタンスリストは、各インスタンスの作成順にソートされ、Candidate MasterはMasterの高可用性オプション使用時点で作成されるため、フェイルオーバー後、インスタンスの順序が変わる場合があります。
> [参考] DBファイル暗号化機能を使用すると、パフォーマンスが多少低下する場合があります。
> [参考]基本アラーム使用時、該当インスタンスに対するアラームが自動的に登録され、名前は"{インスタンス名}-default"に設定されます。登録されるアラームは変更および削除することができ、適用されるインスタンスも変更できます。

**バックアップ&アクセス制御** 画面でバックアップ情報を指定します。

![rds_02_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_02_20210112_jp.png)

* 自動バックアップおよびアクセス制御を設定した後、 **次へ** ボタンをクリックします。
* クエリー遅延待機時間：バックアップ遂行時にFLUSH TABLES WITH READ LOCK遅延待機時間を設定できます。 
  * 0～21600の間の値に設定できます。
* バックアップ保管期間：自動バックアップをするには、1日以上を選択します。
    **なし**を選択すると、自動バックアップが行われません。
* バックアップ開始時刻：自動バックアップはバックアップ開始時刻からDurationの間の任意の時点に始まります。
    * Durationはバックアップが始まる時刻を意味します。 
    * Duration内にバックアップが終了することを意味するわけではありません。
* ユーザーアクセス制御：DBインスタンスにアクセス可能なユーザーをCIDR形式で入力します。
    * ユーザーアクセス制御に登録されていないIPは接続できません。
    * アクセス制御を行う時、方向設定で`受信/送信`を許可するかどうかを選択します。

DB Configuration画面で設定値を変更できます。

![rds_03_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_03_20210112_jp.png)

* 設定値を変更した後、 **作成** ボタンをクリックします。
* 最後に **確認** ボタンをクリックすると、DBインスタンスが作成されます。
* 作成されるまで、数分から数十分かかります。

### DBインスタンス接続

* 作成されたDBインスタンスを選択すると、詳細設定を確認できます。 
* インスタンス[詳細設定]の[接続情報]で、接続可能なドメイン情報を確認できます。
* Floating IPを‘使用’に設定していないDBインスタンスは、外部からアクセスできません。


1. 外部から接続をテストするために右上の **変更** ボタンをクリックします。
2. Floating IP項目を **使用する**に修正します。
3. **確認** ボタンをクリックすると、修正事項が反映されます。

![rds_04_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_04_20210112_jp.png)

* 設定後、Floating IPが作成され、外部からアクセスできることを確認できます。

![rds_05_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_05_20210112_jp.png)

* 次はMySQL Workbenchの接続例です。

![rds_06_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_06_20210112_jp.png)

#### 制約事項

* ユーザーComputeサービスのインスタンスがdnsサーバーに接続できないネットワーク環境の場合、該当インスタンスはドメインを通してRDSインスタンスに接続できません。
* ユーザーが使用中のISPで、セキュリティのためによく知られているポートをブロックすることがあります。NHN CloudのRDSに接続できない場合もあり、その場合はポート番号を変更する必要があります。

## DBインスタンス

### 高可用性

* 別のAvailability ZoneにCandidate Masterを作成しておけば、Masterに障害が発生した時、フェイルオーバーを進行させることができます。
* 高可用性インスタンスを再起動する時、[フェイルオーバーを利用した再起動]オプションを選択し、MasterとCandidate Masterを交換できます。
* 高可用性を使用したインスタンスの場合、一部オプションを変更する時、接続情報は変わりませんが、MasterとCandidate Masterインスタンスは変わる場合があります。
* 障害が発生し、高可用性インスタンスにフェイルオーバーが実行された時、変更された新しいMasterインスタンスは、既存のMasterインスタンスのバックアップを継承しません。

> [参考]高可用性インスタンス使用時、 MySQLクエリーを使用して他のインスタンスまたは外部MySQLのMasterから強制的に複製するように設定すると、高可用性および一部機能が正常に動作しません。

#### 高可用性の一時停止と再開

* 一時的な作業によるMasterインスタンスの接続中断や大量の負荷が予想される状況で、一時的に高可用性機能を停止できます。
* 高可用性機能が一時停止すると、障害を検知しません。したがってフェイルオーバーが行われません。
* 高可用性機能が一時停止している態でインスタンスの変更や再起動を行うと、一時停止した高可用性機能を再開します。
* 高可用性機能が一時停止しても、データの複製は正常に行われますが、障害が検知されないため、長時間一時停止状態にすることは推奨しません。

#### 制約事項

* 高可用性インスタンスは、最初の1回のフェイルオーバーを保障します。障害が発生してフェイルオーバーした場合、Candidate Masterインスタンスが高可用性機能を使用しない一般Masterに変更されます。
* 変更された新しいMasterインスタンスは、既存Masterインスタンスの接続に使用されるドメインを継承します。
* また、高可用性オプションを新たに指定して使用できます。
* フェイルオーバーを行った既存のMasterインスタンスは、接続情報が変更され、’中止’状態に変わります。
* フェイルオーバーを行った既存のMasterインスタンスは、インスタンス再起動機能を利用して再起動を試行できますが、障害によるデータ損失などの理由で再起動できなかったり、正常に作動しない場合があります。
* Read Only Slaveインスタンスには高可用性機能を提供しません。
* 高可用性機能を使用するインスタンスを再起動したり、オプションを変更する間は、該当インスタンスのRead Only Slave操作ができなくなります。
* 高可用性機能はドメインを基盤にしています。そのため、ユーザーのComputeサービスのインスタンスがDNSサーバーに接続できないネットワーク環境の場合、該当インスタンスはドメインを通してRDSインスタンスに接続することができず、障害措置発生時、正常に接続できません。


### インスタンスタイプ

* NHN Cloud ComputeおよびNetworkのサービスで提供中のインスタンスタイプから選んでDBインスタンスを作成できます。

### バックアップ

* RDSでは、すべてのバックアップを実行した後、作成したバックアップを独自のObject Storageにアップロードして保管します。
* 自動バックアップに限り、原本インスタンスのデータボリュームサイズ分のバックアップ容量を無料で提供します。
* 別途料金を希望しない場合は、バックアップ周期を調整する必要があります。
* バックアップの実行中は、性能が低下することがあります。
* サービスに影響を与えないようにするには、サービスの負荷が小さい時間にバックアップを行ってください。
* NHN Cloud RDSは時点復元をサポートします。
    * バイナリログ(binary log)サイズと保管周期が短すぎる場合、希望する時点に復元するのが困難な場合があります。
* 復元中のDBインスタンスはバックアップできません。

#### 自動バックアップ

* DBインスタンスのバックアップ周期を1日以上に設定すると、自動バックアップが有効になります。
    * バックアップ周期を1日以上から、なしに変更すると、即時にすべての自動バックアップはサーバーから削除されます。
    * 削除されたバックアップは復元できません。
* 設定されたバックアップ周期分、バックアップファイルを維持します。
* 自動バックアップは、バックアップ開始時刻からDurationの間の任意の時点に始まります。
* Durationはバックアップが始まる時刻を意味します。 Duration内にバックアップが完了するということではありません。
    * Duration内にバックアップを完了できなくてもバックアップは終了しません。
* 自動バックアップは、原本インスタンスを全て削除する場合、一緒に削除されます。

> [参考] MySQL 5.7以上ではバックアップ中にインデックス作成や、再度ビルドを行うとバックアップに失敗します。

#### 手動バックアップ

* 自動バックアップ以外に、いつでも手動でバックアップできます。
* 手動バックアップは、明示的に削除しない限り削除されません。

### 復元

* 保管されたバックアップを利用して、希望する時点にDBインスタンスを復元できます。
* 復元時、原本DBインスタンスを変更せず、新しいDBインスタンスを作成します。
* バックアップの保存位置がObject Storageにある場合、さらに時間がかかります。
* バックアップ中のDBインスタンスを利用して復元できません。
> [参考]復元の進行中、Binary Logファイルのサイズ分、Object Storage使用量が発生することがあります。
> [参考]バイナリログファイルがない時は、時点復元ができません。

### コピー

* 読み取り性能高めるには、MySQLがサポートするRead Only Slaveを作成します。
* Read Only Slaveを作成するには、原本DBインスタンスを選択した後、 **追加機能 > コピー作成**を選択します。

![rds_07_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_07_20210112_jp.png)

* コピー作成のための詳細設定を入力し、 **コピー** ボタンをクリックすると、コピーが作成されます。
* コピー元DBインスタンスと同じタイプまたはさらにスペックの高いタイプでの作成を推奨します。スペックの低いタイプで作成した場合、コピー作成処理に遅延が発生することがあります。
* コピー作成時、コピー元のDBインスタンスのI/O性能が通常より低下することがあります。
* コピー元のDBインスタンスのサイズに比例して、コピー作成時間が増加することがあります。
> [参考]コピーの進行中、バイナリログファイルのサイズ分、Object Storage使用量が発生することがあります。
> [参考]複製が完了すると、Masterインスタンスのアクセスルール(access rule)項目にRead Only Slaveのルールが追加されます。 

#### 制約事項

* 1つの原本インスタンスは、最大5個のコピーを作成することができます。
* コピーのコピーは作成できません。

### 昇格

* コピー関係を切り、Read Only SlaveからMasterに変更することを昇格と呼びます。
* 昇格したコピーは、原本DBインスタンスの修正事項を自動的に反映しません。
* 昇格したコピーは、独立したDBインスタンスとして動作するようになります。
* 昇格するコピーと原本DBインスタンスの間にコピー遅延がある場合、遅延がなくなるまで昇格されません。

### 容量の確保

*  DBインスタンスのリソースを削除し、ディスク容量を確保できます。

#### バイナリログ削除

![rds_08_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_08_20210112_jp.png)

* バイナリログファイルを削除してディスクスペースを確保します。

>[注意]選択した対象バイナリログファイルと、それ以前に作成されたバイナリログファイルがすべて削除されます。
>[注意]バイナリログファイルを削除した時、削除したバイナリログファイルによっては特定時点に復元できない場合もあります。
>[注意]バイナリログファイルを全て削除した時は、時点復元を使用できません。


### ストレージ拡張

![rds_09_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_09_20210112_jp.png)

* DBインスタンスのストレージサイズを拡張します。
* Read Only Slaveが存在する場合、Masterと同じストレージサイズに拡張されます。
* 対象DBインスタンスの再起動を伴います。

### DBファイルの暗号化

* ユーザーデータが保存されるデータベースファイルおよびバックアップファイルを暗号化します。

> [参考]リアルタイムに暗号化を行うため、DBインスタンスのパフォーマンスが多少低下する場合があります。

#### 制約事項

* DBファイルの暗号化機能を使用しないインスタンスから復元または複製をした時、DBファイルの暗号化機能を有効にできません。
* DBファイルの暗号化機能を使用するインスタンスから復元また複製をした時、DBファイルの暗号化機能を無効にできません。

### DBスキーマ& DB User管理

* DBスキーマとDB UserをWebコンソールで管理できます。

> [参考] DBスキーマとDB Userをクエリーで作成、修正、削除できません。
![db_schema_and_user_list_20210209_ko](https://static.toastoven.net/prod_rds/21.03.09/rds_01_20210309_jp.png)

* **変更**ボタンを押すと、DBスキーマとユーザーを変更できるようになります。

![db_schema_and_user_modify_20210209_ko](https://static.toastoven.net/prod_rds/21.03.09/rds_02_20210309_jp.png)

* **追加**ボタンを押すと、DBスキーマとDB Userの変更事項が一度に適用されます。
* DBスキーマの名前変更はサポートしません。
* DB Userの権限は4個の権限で構成されます。
  * READ：データを照会できます。
  * CRUD：READ権限に加えてDMLクエリを実行できます。
  * DDL：CRUD権限に加えてDDLクエリを実行できます。
  * CUSTOM：既存ユーザーの権限です。 CUSTOM権限に変更することはできず、CUSTOM権限のユーザーは削除のみ可能です。

> [注意] 2021.2.16以後に作成されたRDS for MySQLインスタンスは、Webコンソールからのみuserを追加いただけます。
> これはMySQLのバグに起因し、当サービスで採用しているバックアップソリューションによる複製が中断されるための回避策となります。
> CLIによる操作を希望の場合、カスタマーサポートまでお問い合わせください。

> また、2021.2.16以前のインスタンスではCLIによる操作も可能ですが、Read Only Slaveを持っていたり、高可用性インスタンスを有効化している場合、
> CREATE USER、 ALTER USER、 GRANTに関わる作業後にflush privilegesを実行することで上述のバグによる中断が回避されます。
* 下記のDB Userはポリシー上使用できません。
  * mysql.session
  * mysql.sys
  * sqlgw
  * admin
  * etladm
  * alertman
  * prom
  * rds_admin
  * rds_mha
  * rds_repl

* DBスキーマとDB User項目の**同期化**ボタンを押すと、 DBインスタンスに作成されたDBスキーマとDB User情報をそれぞれ取得できます。

### モニタリング項目

* RDSでサポートするモニタリング項目は次のとおりです。

![rds_12_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_12_20210112_jp.png)

## ログファイル

* DBインスタンスに接続しなくても、ログファイルの閲覧やダウンロードができます。
* **DB Instance**を選択した後、**Events & Log**タブを押すと、設定に応じてerror.log、slow_query.log、general.log、server_audit.logファイルを確認できます。

![rds_13_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_13_20210112_jp.png)

* また、必ず**DB Configuration**でログを残すように設定する必要があります。
* **参照**ボタンをクリックすると、新しいウィンドウでログファイルを閲覧できます。
* ログの長さに入力されたライン数だけ閲覧でき、終わりから512KBサイズのログを閲覧できます。

![rds_14_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_14_20210112_jp.png)

* ログファイル全体を閲覧したい場合、 **ダウンロード** ボタンをクリックして直接ファイルをダウンロードする必要があります。

![rds_15_20210112](https://static.toastoven.net/prod_rds/21.01.12/rds_15_20210112_jp.png)

* **ダウンロード** ボタンをクリックすると、新しいウィンドウが表示されます。
* **取得** ボタンをクリックして少し待つと、 **ダウンロード** ボタンが有効になり、ダウンロードできるようになります。
* ログファイルは臨時Object Storageにアップロードされ、最大5分間ダウンロードできるようになります。
> [参考] Object Storageにアップロードされ、削除される5分間にObject Storage使用料金がかかることがあります。

### Audit Log

* DB Configurationの設定を行ってaudit logを残すことができます。
* 作成されたaudit logファイルは、Event & Logタブで確認、ダウンロードできます。
* 詳細な設定値は、次のサイトで確認できます。
  * https://mariadb.com/kb/en/mariadb-audit-plugin-options-and-system-variables

> [注意] MySQL 5.7.15, 8.0.18, 8.0.23 バージョンはサポートしません。

## イベント

![event_list_0_ko](https://static.toastoven.net/prod_rds/210615/event_list_0_ko.png)

DBインスタンスに関連するさまざまな作業中に発生する各種イベントおよび通知グループの監視設定結果を確認できます。

* ❶イベントタイプを選択して照会できます。
* ❷イベントソースまたはメッセージを検索できます。
* ❸イベント発生期間を選択できます。

### イベント購読

![event_sub_list_0_ko](https://static.toastoven.net/prod_rds/210615/event_sub_list_0_ko.png)

イベント購読状況を照会できます。

* ❶ **購読名**または**イベントソース**で検索できます。
* ❷イベント購読を新規で作成できます。
* ❸修正したい購読を選択して購読内容を修正できます。
* ❹削除したい購読を選択して削除できます。

### イベント購読の登録および修正

![event_sub_popup_0_ko](https://static.toastoven.net/prod_rds/210615/event_sub_popup_0_ko.png)

* ❶イベント購読名を入力します。
* ❷イベント購読を行いたいタイプを選択します。タイプによって選択できるイベントコードおよびイベントソースが制限されます。
* ❸イベント購読を行いたいコードを選択します。
* ❹イベント購読を行いたいソースを選択します。
* ❺通知が送信されるユーザーグループを選択します。グループを選択しない場合は通知が送信されません。
* ❻有効/無効を選択します。

## サーバーダッシュボード

![server_dashboard_0_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_0_ko.png)

各種性能指標をチャート形式で確認できます。

* ❶インスタンス名またはIPアドレスで検索できます。
* ❷条件にマッチするサーバーが表示されます。サーバーの状態に応じて右上のアイコンの色が変更されます。
  * 緑色：正常状態
  * 赤色：エラー状態
  * 灰色：削除されたサーバー
* ❸レイアウトを選択できます。
* ❹レイアウトを修正、削除できます。 
* ❺レイアウトを作成するポップアップが表示されます。
* ❻レイアウトにチャートを追加できます。
* ❼照会期間を現在時刻に設定した後、チャートを更新します。
* ❽照会期間を変更できます。
* ❾チャートが表示されます。

### チャート追加

![server_dashboard_chart_add_1_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_chart_add_1_ko.png)

* ❶チャートを追加したいレイアウトを先に選択します。
* ❷チャート追加ボタンをクリックすると、以下のようにチャート追加ポップアップが表示されます。

![server_dashboard_chart_add_2_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_chart_add_2_ko.png)

* ❶追加しようとしているチャートが表示されます。
* ❷追加しようとしているチャートを選択できます。

### チャート修正

![server_dashboard_1_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_1_ko.png)

* ❶チャートの上部領域をマウスでドラッグしてチャートを移動させることができます。
* ❷チャートを削除できます。
* ❸チャート右下をマウスでドラッグしてチャートのサイズを変更できます。

### レイアウト追加

![server_dashboard_layout_create_0_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_layout_create_0_ko.png)

* ❶レイアウト作成ボタンをクリックします。
* ❷レイアウト名を入力します。

### レイアウトの修正および削除

![server_dashboard_layout_modify_0_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_layout_modify_0_ko.png)

* ❶管理ボタンをクリックします。
* ❷レイアウトを修正することができる編集画面に変更されます。
* ❸レイアウトを削除できます。

![server_dashboard_layout_modify_1_ko](https://static.toastoven.net/prod_rds/210615/server_dashboard_layout_modify_1_ko.png)

* ❶確認ボタンをクリックすると変更事項が保存されます。
* ❷キャンセルボタンをクリックすると変更事項がキャンセルされます。

## ユーザーグループ

通知グループおよびイベント購読を通して通知を受けるユーザーをグループで管理できます。

### ユーザーグループ作成

![user_group_create_0_ko](https://static.toastoven.net/prod_rds/210615/user_group_create_0_ko.png)

* ❶ユーザーグループ作成ボタンをクリックするとユーザーグループを作成することができるポップアップが表示されます。

![user_group_create_1_ko](https://static.toastoven.net/prod_rds/210615/user_group_create_1_ko.png)  

* ❷グループ名を入力します。
* ❸通知対象ユーザーが表示されます。**x**ボタンをクリックすると通知対象から除外されます。
* ❹通知対象にユーザーを追加します。
* ❺ユーザーリストのすべてのユーザーを通知対象に追加します。

### ユーザーグループ修正

![user_group_modify_0_ko](https://static.toastoven.net/prod_rds/210615/user_group_modify_0_ko.png)

* ❶修正したいユーザーグループの編集ボタンをクリックすると、ユーザーグループを修正することができるポップアップが表示されます。

![user_group_modify_1_ko](https://static.toastoven.net/prod_rds/210615/user_group_modify_1_ko.png)

* ❷修正したい項目を修正した後、確認ボタンをクリックするとユーザーグループが修正されます。

### ユーザーグループ削除

![user_group_delete_0_ko](https://static.toastoven.net/prod_rds/210615/user_group_delete_0_ko.png)

* ❶削除したいユーザーグループの削除ボタンをクリックします。

## 通知グループ

インスタンスの性能指標に監視設定を追加して通知を受け取ることができます。

### 通知グループ作成

![notification_group_create_0_ko](https://static.toastoven.net/prod_rds/210615/notification_group_create_0_ko.png)

* ❶グループ作成ボタンをクリックします。

![notification_group_create_1_ko](https://static.toastoven.net/prod_rds/210615/notification_group_create_1_ko.png)

* ❷通知グループ名を入力します。
* ❸通知タイプを選択します。複数選択できます。
* ❹有効/無効を設定します。
* ❺監視対象インスタンスを選択します。
* ❻ユーザーグループを選択します。

### 通知グループ修正

![notification_group_modify_0_ko](https://static.toastoven.net/prod_rds/210615/notification_group_modify_0_ko.png)

* ❶修正したい通知グループの編集ボタンをクリックします。

![notification_group_modify_1_ko](https://static.toastoven.net/prod_rds/210615/notification_group_modify_1_ko.png)

* ❷修正したい項目を修正した後、確認ボタンをクリックします。

### 通知グループ削除

![notification_group_modify_2_ko](https://static.toastoven.net/prod_rds/210615/notification_group_modify_2_ko.png)

* ❶削除ボタンをクリックすると、登録された通知グループを削除できます。

### 監視設定を追加

![notification_group_watchdog_0_ko](https://static.toastoven.net/prod_rds/210615/notification_group_watchdog_0_ko.png)

* ❶監視設定を修正したい通知グループの監視設定ボタンをクリックします。

![notification_group_watchdog_1_ko](https://static.toastoven.net/prod_rds/210615/notification_group_watchdog_1_ko.png)

* ❷監視設定ボタンをクリックします。

![notification_group_watchdog_2_ko](https://static.toastoven.net/prod_rds/210615/notification_group_watchdog_2_ko.png)

* ❸監視する項目を選択します。
* ❹比較方法を選択します。
* ❺しきい値を入力します。項目によって入力できる最大値が異なります。
* ❻持続時間を入力します。
* ❼追加ボタンをクリックすると監視設定が登録されます。キャンセルボタンをクリックすると監視設定が登録されません。

### 監視設定の修正および削除

![notification_group_watchdog_3_ko](https://static.toastoven.net/prod_rds/210615/notification_group_watchdog_3_ko.png)

* ❶編集ボタンをクリックすると監視設定を修正できます。
* ❷削除ボタンをクリックすると監視設定を削除できます。

## ユーザー権限の分離

* プロジェクトメンバーの権限をRDS for MySQL ADMIN / RDS for MySQL MEMBERに区分して付与できます。
* RDS for MySQL ADMIN権限は、従来と同じように、すべての機能を使用できます。
* RDS for MySQL MEMBER権限は、情報を照会する機能のみ使用できます。
  * インスタンスの作成、修正、削除など、インスタンスを対象に行うあらゆる機能を使用できません。
  * ただし、Notificationタブでアラームに関連する機能は使用できます。

## 付録1. ハイパーバイザメンテナンスのためのDBインスタンスマイグレーションガイド

NHN Cloudは周期的にDBインスタンスのハイパーバイザソフトウェアをアップデートしてセキュリティと安定性を向上させています。
メンテナンス対象ハイパーバイザで起動中のDBインスタンスは、マイグレーションを通してメンテナンスが完了したハイパーバイザに移動する必要があります。

DBインスタンスのマイグレーションはNHN Cloudコンソールで開始できます。
DB構成に応じて特定DBインスタンスを選択してマイグレーションする時、関連するDBインスタンス(例えばSlaveインスタンス)もメンテナンス対象の場合は一緒にマイグレーションを進行します。
下記のガイドに従ってコンソールにあるマイグレーション機能を利用してください。
メンテナンス対象に指定されたDBインスタンスがあるプロジェクトに移動します。

### 1. メンテナンス対象DBインスタンスを確認します。

名前の横にマイグレーションボタンがあるDBインスタンスがメンテナンス対象のインスタンスです。

![rds_planed_migration_0](https://static.toastoven.net/prod_rds/planned_migration_alarm/image0_ja.png)

マイグレーションボタンにマウスオーバーすると、メンテナンス日程の詳細を確認できます。

![rds_planed_migration_1](https://static.toastoven.net/prod_rds/planned_migration_alarm/image1_ja.png)

### 2. メンテナンス対象DBインスタンスに接続中のアプリケーションソフトウェアを終了する必要があります。

DBに接続しているサービスに影響を与えないように、適切な措置を取ってください。
やむを得ずサービスに影響を与えてしまう時は、NHN Cloudサポートに連絡してくだされば、適切な措置を案内いたします。

### 3. メンテナンス対象DBインスタンスを選択してマイグレーションボタンをクリックし、DBインスタンスマイグレーションの確認ウィンドウが表示されたら確認ボタンをクリックします。

![rds_planed_migration_2](https://static.toastoven.net/prod_rds/planned_migration_alarm/image2_ja.png)

### 4. DBインスタンスのマイグレーションが終わるまで待機します。

DBインスタンスの状態が変更されない場合は「更新」を行ってください。

![rds_planed_migration_3](https://static.toastoven.net/prod_rds/planned_migration_alarm/image3_ja.png)

DBインスタンスのマイグレーション中は何も操作ができません。
DBインスタンスのマイグレーションが正常に完了しなかった場合、自動的に管理者に報告され、NHN Cloudから別途連絡いたします。
