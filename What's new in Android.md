# [What's new in Android](https://io.google/2022/program/4e81975b-46a2-4966-98d8-19fb4fb66f78/)

* Jetpack
  * JankStats
    * alpha
  * Room
    * 2.5
      * Kotlinで書き直される
      * KSPサポート
  * Navigation
     * multiple backstackサポート
      * コードの変更は不要
  * 詳細は`What's new in Jetpack`で
  * Fragment
    * Fragment Result
    * 詳細は`Fragments, The Good(non-deprecated) Parts`で
  * Compose
    * 1.2 beta
      * Downloadable Fonts
      * Nested Scrolling Interop
      * Lazy grids
        * 1.2でexperimentalからstableへ
        * Staggered grids はまだ
    * Tools
      * Live Edit
      * Recomposition debugging
      * Compose Animation Preview
    * 詳細は`Common Performance Gotchas in Jetpack Compose`, `Lazy Layouts in Compose`で
    * ワークショップは`Basic Layouts in Compose`, `Using State in Jetpack Compose`が用意されている
  * Large Screens
    * `Designing Apps for Large Screens`
      * Canonical layouts
        * 1:1 layouts
        * 1:2 layouts
    * `Update your app for the larger screens`
      * WindowManager 1.1
      * Compact 600dp Medium 840dp Expanded という値
      * FoldableはActivity embedding
      * SlidingPanelLayout
      * Navigation Rail
      * Jetpack DragAndDropライブラリのbetaがリリース
    * `Update your app for the larger screen`
      * Desktop Emulator
    * `Implementiong Android apps for all screen sizes`
       * Compact -> navigation bar
       * Medium -> navigation rail
       * Expanded -> navigation drawer
    * `Input for all screens`
      * Keyboard shortcuts
        * Tabでのフォーカス移動
          * `nextFocusForward`
      * Hover States
      * Stylus
    * `Building Adaptive Layouts with SlidingPaneLayout`
    * d.android.com/large-screens
* Android 13
  * 現在beta2
  * `Developer Privacy User Centric Apps`
    * `Notification Permission`
      * Notificationの表示に権限をリクエストが必要になる
    * Photo Picker
      * `READ_EXTERNAL_STORAGE`などの権限なしで写真にアクセスできる
      * Android 11, 12でも利用可能
      * Google Play Systemの更新で継続的に改善される
  * `Overview of the Privacy Sandbox on Android`
    * SDK Runtime Proposal
    * Topics Proposal
    * Attribution Reporting API
  * `Back to the basics of System Back`
    * `KEYCODE_BACK`, `onBackPressed`が使われなくなり`OnBackInvokedCallback`で全体を管理する
    * `enableOnBackInvokedCall`でオプトインできる
    * Android 14からはデフォルトで有効化される
    * 有効にするとアプリが終了することが視覚的にわかりやすくなる
  * `Managing background work on Android`
* `What's new in Android Machine Learning`
  * MLKit
  * Supporting Components
  * Text Recognition V2
    * beta
    * 37 Languages サポート
  * Google Code Scanner
    * Google Play Servicesによって提供
    * カメラの権限のリクエストが不要
  * TensorFlow Lite in Google Play Services
    * アプリサイズを減らせる
* `What's new in Android Camera`
  * CameraX
    * test labは継続的に拡大している
    * HDR Video Capture
      * Android 13の新機能
    * Extensions
      * 選ばれたデバイスで先行して進められてから全体で利用可能になる
      * Bokehは今年にリリースされる
* `What's new in Android media`
  * HDRビデオのサポート
  * Rendering of HDR videos requires SurfaceView
    * HDRの変換、編集をサポートするJetpackのライブラリがリリースされる予定
  * Spatial Audio
    * ExoPlayer 2.17で試せる
  * ExoPlayer
    * DRM keyのプリフェッチ(2.14)
    * Android 12に対応(2.16)
      * ダウンロードでのバックグラウンドタスク周り
    * サーバーサイドでの広告の挿入(2.17)
  * Jetpack Media3
    * ExoPlayerからの移行は継続して行われている
    * media3-exoplayer：Playback
    * media3-ui：UI Components
    * media3-session：MediaSessionとの統合
    * media3-common：共通モジュール
    * media3-transformerなど：新しいユースケース
    * **今年、stable版と移行のためのガイダンスがリリース予定**
  * Performance Class
    * Jetpack Core Performance Library
  * ワークショップは`Media Streaming with ExoPlayer`で
    * https://github.com/googlecodelabs/exoplayer-intro
* `What's new in Accessibility for Android Developers`
  * Touch target size
    * Minimum 48 x 48dp
  * Semantics tree
    * Layout Inspectorで確認できるようになる予定
* `Introducing Google Wallet and Developer API Features`
  * Google Pay Passes APIはGoogle Wallet APIに
    * ボタンも`Add to Google Wallet`に変わる
  * New Android SDK
    * バックエンドとの統合は不要
  * developers.google.com/wallet
* Better Together
  * `Multi-device Development`
    * 2022 Q2にEarly Preview APIsがリリース
      * 近くにあるデバイスを探索
      * デバイスの起動
      * セキュアな通信
      * アプリのUXを該当デバイスに移す
  * `Android solutions for seamless sign-in across devices`
    * BlockStore
      * アプリの保存、デバイス間の移行がセキュアかつシンプルにできる
    * OneTap
      * sign-up, sign-inが簡単にセキュアにできる
    * Passkeys
      * Google accountにバックアップ、同期される
      * デバイスの切り替え後のアプリのsign-inが容易になる
* Google Play
  * `App quality on Google Play`
    * Monitor
      * Android Vitals
        * 国ごとの確認ができるように
        * Crashlyticsとのリンクができるように
    * Prioritize
      * Reach and devices
        * どういったスペックのデバイスで発生しているのかがわかる
      * Device Catalog
        * デバイスのモデルやスペックなどをより詳細に確認できるように
  * `Power your success with new acquisition, engagement and monetization tools`
    * Engagement
      * LiveOps(beta)
        * アクティブユーザー数が多いアプリ、収入が多いアプリが表示される
        * Offers
        * Reporting
          * LiveOpによる影響を見れる
    * Monetization
      * Subscriptions
        * より柔軟に
          * Strategic guidance
* TV, Watch, Car
  * `Creating beautiful, power-efficient apps for Wear OS`
    * Compose for Wear OS
      * betaに
    * Health Services
      * デバイス上で管理されるので自分のアプリを構築することに集中できる
      * ExerciseClient
      * PassiveMonitoringClient
      * MeasureClient
      * `Introducing Health Connect by Android`
        * Fitbit, Google Fit, Samsung Healthを1つに
        * Jetpack Health APIはalphaとして提供されている
  * `What's new with Android TV and Google TV`
    * Android 12 recap
      * Framerate switching
      * 4K UI
      * Text scaling
      * Kids profiles
    * Android 13
      * Performance & Quality
        * Anticipatory audio route
        * HDMI state changes
          * HDMIで接続しているデバイスが長時間使われないと一時停止、スタンバイとなる
      * Input & Accessibility
      * Multitasking
        * Picture in picture
        * Expanded Pip API
          * Meetとかのやりとりを人ごとに縦長で表示
        * Keep-clear APIs
  * `What's new with Android for cars`
    * Car App Library
      * 1.3
        * 地図のテンプレートが改善
* Tools
  * `What's new in Android Development Tools`
    * Dolphin
      * beta
    * Electric Eel
      * Canary
  * `What's new in Android Performance`
     * Local
      * Studio Profilers
      * Perfetto
     * CI
      * Jetpack Benchmark
      * Macrobenchmark
        * stable
     * Field
      * Vitals
      * Firebase Performance
      * JankStats
        * alpha
    * Mainling ART
      * Android 12以上であればAndroidのリリーサイクルとは別にARTを更新することができる
      * OpenJDK APIが利用可能
      * パフォーマンス改善
      * バグフィックスが取り込まれる
