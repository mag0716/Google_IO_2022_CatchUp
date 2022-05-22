# [Managing background work on Android](https://io.google/2022/program/477adf14-7c6d-4710-9f19-b127421a396c/)

* Android OSはユーザーと開発者の両方のニーズにバランスを取る必要がある
  * 開発者：スピード、信頼性、エンゲージメント、マネタイズ
  * ユーザー：バッテリー、即座の更新、通知、セキュリティ、プライバシー
* Googleのビジョン
  * 開発者：一貫性があり、ドキュメント化されたAPIがあり、制約を理解できている。効率や信頼性のために正しいツールがある。
  * ユーザー：お気に入りのアプリや機能を確実に動作させながら予測可能なバッテリーを実現
* App Restriction Levels
  * Unrestricted
  * Optimized(default)
    * Active
    * Working Set
    * Frequent
    * Rare
  * Restricted Bucket
    * Android 12で追加され、Android 13で拡張される
  * Background Restricted
    * Foreground Serviceを実行できず、バックグラウンド中はいかなるタスクも実行できない
    * Android 13以上
* JobSchedulerの改善
  * Prefetch Jobs
  * Priority
  * Priority + Device Health
    * デバイスの状態(端末が熱すぎる)によって高い優先度のジョブも実行さ れない
    * 全てのアプリが優先度を高くするのでは？
      * よくない作法
      * 優先度の高いジョブはデフォルトや優先度の低いジョブに比べてタイムアウトが短くなるので優先度の高いジョブを誤った状況で使用することを防ぐことができる
      * 全てのジョブに同じ優先度を設定することに利点がない
        * システムはジョブの区別ができないので本当に重要なジョブが実行が遅れる可能性がある
      * JobSchdulerはジョブが推定するすべてのデータを転送できると確信した時に賢くジョブを実行するように努める
        * `stMinimunNetworkChunkBytes`, `setEstimateNetworkBytes` が提供され、これを利用することでシステムが効率よくジョブを実行できるようにする
  * Expedited Job Improvements
    * トップで実行されているアプリのExpedited Jobが改善され、Foreground Serviceからの切り替えが容易になる
* Foreground Notifications
  * Foreground ServiceはNotificationの許可がなくても実行される
  * Android 13からForeground ServiceのNotificationを削除することができる
* Notification visibility
  * Notificationが見えないServiceは悪用されやすい
    * この問題の対策のためにFGS Task ManagerがAndroid 13から導入される
* High Priority Firebase Cloud Messages
  * Android 13からHigh Priority FCMとStandby Bucketsを分けられた
  * 優先度がダウンレードすることがあるので`getPriority`と`getOriginalPriority`をチェック推奨
* 開発者は何ができるのか？
  * エチケット
    * 全てのエネルギーを消費するな
      * モバイルのエネルギーは非常に限られている
  * Best Practices
    * WorkManagerを利用する
      * `setExpedited(OutOfQuotaPolicy.RUN_AS_NON_EXPEDITED_WORL_REQUEST)`
        * Foreground Serviceはパフォーマンスが高いが効率が悪い
        * WorkManagerはForeground Serviceの代用としてExpeditedが用意されている
      * Constraintsを指定できることでジョブが成功する状態のみジョブを起動することができる
    * High Priority FCM
      * ユーザーに通知で割り込むことが適切なメッセージにのみ利用する
    * データの更新頻度を検討する
      * 更新されたデータを取得したのがどのくらい前であれば適切なのかを考慮する
      * あまり頻繁な取得はバッテリー消費に影響する
    * Bluetoothを効率的に利用する
      * 以下の順で効率がよく、速度が遅い
        * SCAN_MODE_LATENCY
        * SCAN_MODE_BALANCED
        * SCAN_MODE_LOW_POWER
      * 頻繁にスキャンするのをやめる。ユースケースが適さないのであればActivityが表示されている間のみスキャンする
* Efficiency while in use
  * Device thermal state
    * `PowerManager.THERMAL_STATUS_MODERATE`
    * フレーム抜けが発生するリスクを抑えるために解像度を下げるなど対策できる
  * CameraXの利用が強く推奨
    * CameraXではCamera2が利用されており、Camera1 APIよりも効率がよい
  * Display Refresh Rate
    * ゲーム開発者向け
    * 必要以上のフレームレートにしていないか？
      * `Surface.setFrameRate`
