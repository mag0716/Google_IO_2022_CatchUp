# [Creating beautiful, power-efficient apps for Wear OS](https://io.google/2022/program/7f0f4d16-b260-414d-9f2d-bd2e18ea469b/)

* Compose for Wear OS
  * beta
    * 1.0の機能実装は完了しプロダクトで利用するための準備ができた
    * 今年stableがリリースされる
  * Material Design for Wear OS
  * 原則と基本的なコンポーネントはJetpack Composeと共有している
  * Navigation
    * androidx.wear.compose.navigation
    * swipe to dismiss
    * `SwipeDismissableNavHost`
  * `ScalingLazyColumn`
    * androidx.wear.compose.material
    * `autoCentering`
    * `anchorType`
    * `flingBehavior`
  * `Picker`
    * androidx.wear.compose.material
    * `rememberPickerState`
      * `repeatItems`
    * `readOnly`
  * `InlineSlider`
    * androidx.wear.compose.material
    * `segmented`
    * `increaseIcon`, `decreaseIcon`
  * `Stepper`
    * androidx.wear.compose.material
    * `valueProgression`
  * `Dialog`
    * androidx.wear.compose.material.dialog
    * スワイプジェスチャーをサポート
  * `CircularProgressIndicator`
    * androidx.wear.compose.material
    * デフォルトはinfinite progress
    * 進捗率を利用する場合は`progress`に指定する
* Android Studio
  * Electric Eel
    * autoComplete
    * Wear composable Preview
      * `uiMode`
      * `device`
    * Live edit
    * Project template
* 既存アプリにComposeを適用する
  * 新しい画面をComposeで実装する
  * ComposeとAndroid Viewsを共存させる
  * 画面単位でComposeに移行していく
* Horologist
  * github.com/google/horologist
  * Wear OS向けアプリを開発するためのライブラリ
    * Navigation Aware Scaffold
    * Date & Time Pickers
    * Media UI include Playback Control and Volume Screens
* Wear Performance
  * リリースビルドで計測する
  * JankStatsを有効にする
  * Macrobenchmarkで起動時間を計測する
  * Baseline Profilesを利用する
  * ネットワークの利用を意識する
    * ネットワークに接続していない状況でも利用できるようにする
  * 効果的なライブラリを利用する
    * WorkManager
    * Health Services
      * 腕時計のセンサーを利用してデータを収集
      * スマホ側でデータの保存、共有
      * Battery Life
        * アプリごとのアルゴリズムでセンサーからデータ収集していたのをMCUがセンサーとやりとりすることでバッテリー消費を改善
      * Developer Experiences
        * ExerciseClient
          * ランニングやバイクなどの運動を計測するアプリ向け
        * PassiveMonitoringClient
          * 歩数などバックグラウンドでデータを収集する必要があるアプリ向け
        * MeasureClient
          * 心拍数など現在の健康状態の測定するアプリ向け
    * Future Proofing
      * 新しいセンサーが追加されてもアプリはAPI経由で新たなデータにアクセスできる
* リソース
  * d.android.com/wear
