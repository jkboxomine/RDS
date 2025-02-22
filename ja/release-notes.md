## Database > RDS for MySQL > リリースノート

### 2021. 08. 25.

#### 機能改善

* バックアップのためのボリュームディスク使用方法変更と性能改善
* サービスを有効にする時、リージョン別情報同期を改善

#### バグ修正

* 動作と関連がない無効なタイプのイベントを記録するバグを修正
* 高可用性インスタンスの障害措置を進行中にインスタンスの状態と一致しないイベントを記録するバグを修正
* Database Activityチャートにinsert項目がないバグを修正

### 2021. 07. 13.

#### 機能改善

* MySQL 8.0.23バージョンを追加サポート
* イベント購読リストで有効になっているかどうかを確認できるように改善
* 作成したインスタンスがない時、ダッシュボードに作成したインスタンスがないという文言を表示するように改善

#### バグ修正

* 一部モニタリングデータの未収集バグを修正
* ユーザーグループ名が長い場合、イベント購読の登録、通知グループの追加時にUIの外にはみ出るバグを修正
* ダッシュボードドロップダウンを選択した時、メニューが消えずに残る現象を修正

### 2021. 06. 15.

#### 機能改善

* モニタリングシステム改編

#### バグ修正

* ストレージサイズに近いサイズのバックアップで復元する時、復元できない問題を修正
* オブジェクトストレージにバックアップをエクスポートまたはインポートする時、コンテナまたはパスにハングルがある場合、正常に動作しない問題を修正

### 2021. 05. 11.

#### 機能追加

* オブジェクトストレージを利用したバックアップのエクスポートおよびインポート機能を提供
* 強制再起動機能を提供

#### 機能改善

* xtrabackupログファイルを確認してダウンロードできるように機能改善

#### バグ修正

* サービスを有効にした直後にインスタンスを同時に作成する時、インスタンスが作成できないバグを修正
* 高可用性インスタンスのポートとインスタンスタイプを同時に変更する場合、変更が失敗する現象を修正

### 2021. 04. 13.

#### 機能追加

* MySQLバージョン5.6.33～5.7.26の監査ログ(audit log)機能を提供

#### 機能改善

* プロジェクトメンバーの権限をRDS for MySQL ADMIN / RDS for MySQL MEMBERに細分化
* MySQLがダウンした状態で再起動ができないように修正
* 任意のアベイラビリティゾーンを選択できるように修正
* アラーム設定時に表示されるクォーター制限文言を修正
* RDSで提供するプロシージャの使用方法ガイドを追加

#### バグ修正 

* フェイルオーバーが完了したインスタンスの状態が正常化しない問題を修正
* 作成に失敗したRead Only Slaveが原因で、マスターインスタンスの一部機能が動作しない問題を修正
* データ暗号化インスタンスが強制再起動する時、MySQLが正常に実行できない問題を修正

### 2021. 03. 09.

#### 機能改善
- プロジェクト別リソースクォーター制限機能を改善

#### バグ修正
- 特定の状況でインスタンスの再起動が正常に行われないバグを修正

### 2021. 02. 16.

#### 機能追加

- DB UserとDBスキーマをWebコンソールから制御できる機能を追加

#### 機能改善

- DBファイル暗号化機能を選択した時、ツールチップを提供
- クエリー遅延待機時間の値が異常な場合、検証メッセージを表示

#### バグ修正

- プロジェクトメンバーが20人以上の場合、Notificationメンバーに登録できないバグを修正

### 2021. 01. 19.

#### 機能追加

- 高可用性(HA)機能使用時、 Ping Interval(Masterインスタンス状態を確認する時間間隔)を設定できるように機能追加
- 高可用性(HA)一時中止/再開機能を追加
- **Access制御設定** ダイアログボックスで、アクセス制御方向(受信/送信)を設定できるように機能追加
- t2.c1m1 Flavorインスタンス生成ができないように変更
- t2.c1m1 Flavorで既に生成してある一般インスタンスの場合、高可用性に変更できないように変更

### 2020. 12. 15.

#### 機能追加

- --ftwrl-wait-timeoutオプション値をユーザーが設定できるように機能追加

### 2020. 11. 10.

#### バグ修正

- 自動バックアップ作成に失敗する現象を修正
- 期間が満了した自動バックアップの削除に失敗する現象を修正

### 2020. 10. 13.

#### バグ修正

- innodb_buffer_pool_sizeの値が意図した値に修正されない現象を修正
- require_secure_transportの値がonの場合、ha candidate masterインスタンスの複製が失敗する現象を修正
- 大容量インスタンスをバックアップする時、過度な時間遅延が発生する現象を修正

### 2020. 09. 22.

#### 機能追加

- 韓国(坪村)リージョンオープン

### 2020. 09. 15.

#### 機能追加

- モニタリングAPIをサポート

### 2020. 08. 11.

#### バグ修正

- ユーザーVPCサブネットがない場合、異常なサブネットがリストに表示される現象を修正

### 2020. 07. 14.

#### 機能追加

- MySQL 8.0.18バージョンをサポート

### 2019. 12. 10

#### 機能追加

- DBファイルの暗号化機能を追加 (韓国リージョン)

### 2019. 11. 12.

#### 機能改善

- Candidate Masterの障害検知および復旧機能を高度化

#### バグ修正

- 断続的にバックアップができなかった問題を修正

### 2019. 09. 24.

#### 機能改善

- インスタンス作成速度を改善(HAインスタンス基準約28分→約13分)
- フェイルオーバーを利用して再起動した時、時点復元のための新規バックアップを進行できるようにUXを改善
- 基本アラームを使用するかどうかのUIを変更

### 2019. 08. 13.

#### 機能改善

- 高可用性(HA)に関連するイベントログを、より直感的に確認できるように修正

#### バグ修正

- 断続的にDBインスタンスの作成、復元ができない問題を修正
- DBインスタンスの削除アラームメールが送信されない問題を修正

### 2019. 07. 23.

#### 機能追加

- 基本アラーム機能を追加
- モニタリング項目を追加

#### 機能改善

- バックアップ関連イベントはもはやアラムをサポートしません。

### 2019. 06. 27.

#### 機能追加

- 日本リージョンを追加

### 2019. 06. 25.

#### 機能追加

- 高可用性(HA)機能を追加

#### 機能改善

- インスタンス詳細表示画面に表示されるイベント期間を 1 日から 7 日に変更

#### バグ修正

- 時点復元時、復旧可能な時間から復元できるように修正

### 2019. 05. 14.

#### 機能改善

- インスタンス作成および修正時の検証機能を強化
- Notification 通知イベントの全体選択/解除ができる UX を追加

#### バグ修正

- 作成中のインスタンスを削除する際、削除できない問題を修正
- データ保存場所の空き容量が不足している時、データボリュームが変更されない問題を修正

### 2019.03.12

#### 機能改善

- 意味が曖昧、あるいは、見づらいエラーメッセージの改善
- コンソールでtransaction-isolation値を修正できるよう改善

#### バグ修正

- 1TBのDBのバックアップ時間が1日以上かかる可能性を除去

### 2019.02.26

#### 機能追加

- インスタンスデータレポジトリーにSSDボリュームの機能を追加

#### 機能改善

- Notification受信対象をプロジェクトメンバーに設定するように機能を改善。
- x1、u2 flavorの使用が可能になるよう機能改善。

### 2019.01.29

#### 機能改善

- インスタンスボリュームサイズの最大値を1000Gに変更

### 2018.12.14

#### バグ修正

- r2.c8m64 flavor 非表示を修正
- general logが見えない問題を修正
- VPC Subnet選択時のバグ修正

### 2018.12.11

#### 機能改善

- Peering機能の削除
- ユーザーVPC Subnetを利用したネットワーク通信方式え機能を改善

### 2018.10.23

#### 機能改善

- インスタンス作成/復元/コピー時に入力項目の説明文を表示
- mysql transaction_isolationオプションの表示

### 2018.10.16

#### 機能追加

- インスタンスFlavorの変更機能を追加
- インスタンスStorageの拡張機能を追加

### 2018.08.28

#### 機能追加

- Binary Logファイルの削除によるインスタンス容量確保機能を追加

### 2018.07.24

#### 機能追加

- MySQL 5.7.15バージョンを追加サポート

#### バグ修正

- MySQL 5.7.19バーじょインスタンスを作成時、floating ipをつけないと作成できない問題を修正
- 特定の状況における自動バックアップの時間が通常の2倍になる問題を修正

### 2018.05.29

#### 機能追加

- MySQL 5.7バージョンを新規サポート

### 2018.04.24

#### 機能改善

- masterのport変更時、read only slaveのmaster接続情報を自動変更
- バックアップ後、残賊する不要なログを削除

#### バグ修正

- 検索結果ページ > インスタンス作成後、ページ移動を試みた際、検索結果ページに移動する問題を修正
- パスワード確認欄を空白でインスタンス作成を試みた場合、警告メッセージが表示されない不具合を修正

### 2018.03.22

#### バグ修正

- バックアップ保管期間 ‘なし’に変更した場合、一定時間リストに表示される事象を修正
- インスタンス設定を修正していないのに、インスタンス状態が変更中として表示される問題を修正
- インスタンス再起動時、QPSが負の数で表示される不具合を修正
- Monitoring画面で期間設定のボタンをクリックすると、画面の日付と時刻の更新なしにデータだけが更新されるバグを修正

### 2018.02.22

#### 新商品発売

- TOAST Relational Database Service (RDS)は、Relational Databaseをクラウド環境で提供する商品です。
- 複雑な設定をしなくても、Relational Databaseを使うことができます。
- MySQL 5.6.33バージョンを提供します。
