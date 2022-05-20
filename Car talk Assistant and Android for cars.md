# [Car talk: Assistant and Android for cars](https://io.google/2022/program/089c863e-b885-4f86-a20a-79a1f8702fd5/)

* Assistant Driving Mode
* **Android Auto**
* **Android Automotive OS**
* Overview App for Android for Cars
  * 車向けのアプリの開発には考慮することが多い
    * さまざまな車載デバイスの要素
    * 入力
    * ドライバーの安全を重視
  * Car App Library
    * 上記を考慮し、開発をシンプルにするためのライブラリ
    * 1ソースでAndroid Auto, Android Automotive OSに対応
    * 提供されるUIはドラーバーの安全を考慮している
    * 音声での操作
    * App Category
      * カテゴリごとにテンプレートを用意
      * ナビ、駐車、充電用のアプリをサポート
    * Architecture
      * Android Auto / Automotive OS Host が CarAppServiceに接続
        * CarAppService.onCreateSession()
        * Session.onCreateScreen()
        * Screen.onGetTemplate()
      * Template
        * Generic
          * Search
          * Sign in
          * Grid
          * Message
          * Pane
          * List
          * Long message
        * Navigation
        * Parking and Charging
          * 地図上に位置を表示
* Overview App Actions
  * 車向けにサポートされているBuilt-in Intents(BII)
    * GET_PARKING_FACILITY
    * GET_CHARGING_STATION
  * 実装方法
    * マニフェストファイルに`android.app.shortcuts`を定義
    * `activity-alias`で`androidx.car.app.activity.CarAppActivity`を定義
      * deep Linkを定義
    * shortcut.xmlにBIIを`capability`で定義
  * deeplinkで起動
    * セッション生成前は`Session.onCreateScreen()`
    * セッション生成後は`Session.onNewIntent()`
    * いずれもdeeplinkのUriから必要なパラメータを取得する  
* Displaying Android Widgets on Android for Cars
  * 全てのBIIがWidgetをサポートしているわけではない
  * `capability`の追加、修正
    * `app-widget`を追加
      * 音声でユーザーに通知するために`hasTts`を`true`にする
    * パラメータなしの場合に実行するfallback intentを追加
  * Widgetの生成処理を更新
    * Widget Extension libraryを追加
      * `com.google.assistant.appactions:widgets`
      * BIIの名前、パラメータの抽出に利用
    * TTSのカスタマイズ
      * `AppActionsWidgetExtension`を生成し、`updateWidget`を呼び出す
      * 通常のWidget用の`updateAppWidget`は別途必要
* ドキュメント
  * g.co/androidforcars
  * goo.gle/appactions-docs
