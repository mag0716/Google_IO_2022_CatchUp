# [Google Assistant functionality across Android devices](https://io.google/2022/program/12cb5274-2781-4f3e-95b8-e21eaed2aa67/)

* Assistant + Android
  * USでは1世帯平均11個ののデバイスを接続している(2019年)
  * 2021年には25個に増えた
  * Assistant understands
    * App capabilities
    * Which apps best fulfill user requests
  * Assistant provides consistency through
    * Voice or touch-based requests
    * Single or multi-step journeys
* App Actions
  * 音声コマンドをトリガーにしてアプリの特定機能を起動する
  * 内蔵されたコマンドは60以上
    * BII(Built-in Intents)
    * 例. actions.intent.OPEN_APP_FEATURE
  * Custom Intents
    * 複数の音声コマンドを`string-array`として定義する
  * アクションの結果
    * アプリを起動
    * Widgetsに表示
  * Brandless queries
    * 特定のアプリを指定しない音声コマンド
      * 例. Hey Google, open ExampleFeature
      * 例. Strava
        * `Start my run`で時間のカウントが開始される
  * App Install Suggestions
    * 特定の機能をもったアプリがない場合はインストールを勧める
      * 例. `Show me recipes on TikTok`でPlay StoreでTikTokのページを表示する
  * Smarter Custom Intents
    * `Schedule an appointment`を定義しておくだけで自動的に該当するコマンドを増やしてくれる
      * 例. Reserve, Set, Book, Line up など
  * Wear OS
    * スマホを手に持っていない時でもWear OSデバイスから起動することができる
    * Health & Fitness Built-in Intents
    * 例. `Start my run`でWear OSデバイス上で時間のカウントが始まる
  * Automotive
    * App Actions + Car App Library
      * Android Auto, Android Automotive OSのいずれでも動作する
      * Car App Library Templates
        * Safe driver design
        * Consistent UIs
      * BII
        * GET_PARKING_FACILITY
        * FIND_CHARGING_STATION
  * Media
    * Media Sessionを実装していればTransportControlsを通じて再生状態の変更を行える
* 詳細
  * `How Google Assistant's architecture powers voice features in your apps`
  * `Car Talk: Assistant and Android for Cars`
  * `Integrate Android widgets with Google Assistant`
* ドキュメント
  * goo.gle/appactions-docs
  * goo.gle/appactions-codelabs
  * goo.gle/appactions-samples
  * goo.gle/appactions-videos
