# [What's new in Jetpack](https://io.google/2022/program/c7710536-a86d-42a6-b43e-e69ae76dbb34/)

* Architecture
  * Room
    * KSPでのパフォーマンス改善(2.4.0)
    * Kotlin 1.6をサポート
    * Kotlinで書き直された(2.5.0)
    * Paging 3.0をサポート
    * relational query methodsをサポートし複数の型を返却できるようになった
  * Paging
    * Rx, Guavaサポートがstableに
    * 不正なデータの扱いが改善
    * より包括的なコールバックに
    * codelabが追加
  * Navigation
    * Jetpack Composeとの統合
    * Multiple Back Stacksサポートがstableに
    * two-pane layoutsのサポート
    * Kotlinで書き直された
  * DataStore
    * https://goo.gle/mad-skills-datastore
* Performance
  * JankStats
    * API Level 16まで互換性がある
    * 内部の経験則を利用してパフォーマンス問題を特定する
    * ユーザーの状態やアクションにデータを割り当てるためのUIコンテキストを提供
    * リスナを通じてフレーム毎にレポートする
  * Baseline Profiles
    * カスタムルールをアプリやライブラリに提供
    * 起動時のパフォーマンス向上
    * 人気のJetpackライブラリにプロファイルを追加
      * Fragments, Compose
  * Macrobenchmark
    * API Level 23までサポート
    * TraceSectionMetricでカスタムしたタイミングでの計測を追加
    * AudioUnderrunMetricでオーディオのバッファリングを計測
    * クリティカルなワークフロー用のプロファイルをBaselineProfileRuleで生成できる
    * https://d.android.com/studio/profile/baselineprofiles
  * Tracing
* UI
  * WindowManager
    * Foldableサポート
    * 特定エリア(物理的なヒンジなど)にコンテンツの配置を避ける
    * SlidingPaneLayoutとの統合
  * DragAndDrop
    * alpha
    * API Level 24までサポート
  * AppCompat
    * 最新の絵文字がEmoji2に統合
      * API level 14以上で利用可能
    * Android 13で追加されたカスタム言語設定がTiramisuまでバックポートされる
    * 追加のロケールをダウンロードするためにPlay splitsが使用される
      * `AppLocalesMetadataHolderService`
      * Android 13からだがオーバーヘッドなしにプラットフォームが自動的に行なってくれる
* Compose
  * Google Play, Twitter, AirBnbでも利用されている
  * Nested Scrolling Interop
    * collapsing toolbarの実装も容易になる
  * Downloadable Fonts
  * Lazy Layouts
    * 詳細は`Lazy Layouts in Compose`で
  * Tools
    * 詳細は`What's New in Android Studio`で
  * Android Basics with Compose
    * g.co/android/basics-compose
* Other Announcements and Additional Talks
  * Annotation
    * Kotlin用に移行された
      * @ReturnThis
      * @OpenForTesting
      * @EmptySuper
      * @DeprecatedSinceApi
