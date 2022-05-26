# [Multi-device development](https://io.google/2022/program/2d35bc51-fef8-4f4f-830f-0dba6d30e592/)

* なぜマルチデバイスでの開発が重要なのか？
  * 現在ユーザはより多くのデバイスを接続しており、相互に作用できるポテンシャルを持っている
  * ユーザーがより多くのデバイスを利用しようとすると複雑さが増してくる
* マルチデバイスを対応する上での開発者が解決しないといけないこと
  * デバイス間の相互作用
  * デバイスごとのサインイン
  * 奥地区、計測、テストが困難
* プラットフォーム
  * UWB, BLE, Wi-Fiを活用
    * UWB APIsがJetpackとして新たに追加される
      * 位置、方向などへのアクセスや他のデバイスとの接続
  * Nearby
    * https://developers.google.com/nearby
  * Business Logic
    * 接続方法(Bluetooth, UWB, Wi-Fi)の隠蔽
    * デバイス間の双方向コミュニケーション
    * Android 8までの後方互換
    * Android以外のプラットフォームのサポート(ChromeOS, iOS, Windowsなど)
* Cross devices APIs
  * ユースケース
    * Personal experiences
      * テレビで映画のレンタルや購入をする際にスマホで支払い方法を入力する
      * スマホで読み始めた長文をタブレットで読み終えてもスマホ側で読み終えた場所を同期させる
    * Communal experiences
      * 同乗者として地図上の位置を運転手と直接共有する
      * サイクリングコースを一緒にサイクリングしている人と共有する
      * グループ内でメニューのオーダーを集める
  * APIs
    * 2022 Q2にearly previewが公開される
      * スマホ、タブレット、TV、WearOSがまずは対象
    * Device Discovery
      * フィルタリングできる
        * 同じGoogle account
        * デバイスの種類
        * 手動でのペアリング
    * Device wake-up
      * デバイスがスリープ中でもデバイスが起動する
      * `onNewIntent`が起動する
    * Secure Communications
      * 認証方法
        * Google accounts
        * 証明書
        * 手動でのペアリング
    * Multi-device sessions
* 詳細
  * d.android.com/better-together
  * https://github.com/android/connectivity-samples
