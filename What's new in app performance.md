# [What's new in app performance](https://io.google/2022/program/2cf473b7-113e-4332-a469-8dfd815eb45b/)

* Performance tools
  * Perfetto
    * adbを利用してパフォーマンス情報を収集できる
      * Android Studioが不要
    * WebベースのUIツール
      * https://ui.perfetto.dev/
  * Android Vitals
    * Google Play Consoleの一部で実際のデバイス上でのパフォーマンス改善に役立つ
* App Startup
  * Cold start
    * プロセスの作成
    * ContentProviderの初期化
    * Application#onCreate
    * 5秒以下が望ましい
  * Warm start
    * Activity#onCreate
    * View階層の生成
    * 2秒以下が望ましい
  * Hot start
    * Activity#onStart
    * 1フレーム目の描画
      * Measure
      * Layout
      * Render
    * 1.5秒以下が望ましい
  * States
    * TTID(Time to initial display)
      * プロセスが生成され1フレーム目が描画されるまで
      * `ActivityManager: Displayed`
    * TTFD(Time to full display)
      * データが読み込まれユーザが操作可能になるまで
      * `ActivityManager: Fully drawn`
  * アプリ起動速度改善の重要性
    * 例. Google Map
      * 30%の改善で2.4%の検索率上昇
    * 例. Josh
      * 30%の改善で1millionのユーザーの獲得
    * 例. Zomato
      * 30%の改善で1日のユーザーが90%増え、オーダーが600,000以上増えた
  * Macrobenchmark
    * アプリ起動時のデータの取得
    * 大きい画像のパフォーマンス監視
    * 1度のみ、継続した実行の選択
    * 起動Statesの選択
    * 難読化は不要
    * サンプル：https://github.com/android/performance-samples/tree/main/MacrobenchmarkSample
* Baseline profiles
  * アプリ起動速度の改善
  * Jankyフレームの現象
  * クリティカルなユーザー操作をカバー
  * 使い方
    * Profile Generator
      * Macrobenchmarkでのテストに特化
      * app/src/mainに配置
    * Profile installer
      * アプリインストール時にプロファイラのインストール
  * App Startup Library
    * リソースの競合を避ける
    * コンポーネントの初期化
      * 例. WorkManager
* Jank monitoring
  * 改善の重要性
    * 例. ShareChat
      * フレーム落ちを45%改善でユーザーエンゲージメントが10%改善
    * 例. Jio
      * 起動速度を35%、ANRを40%改善でよいレビューが20%増加、アンインストールを5%減少
    * 例. OkCredit
      * ANRを50%改善でユーザー維持を20%、取引数が30%増加
  * Microbenchmark
    * Test frequently run code
    * Get statistically significant data
    * Obtain consistent results
    * 1.1.0での新機能
      * Allocation counting
      * Profiling support
        * Android Studioで読み込む
        * build script内で設定できる
      * Faster setup
        * Android Studioでセットアップができる
        * モジュールの作成フローでBenchmarkが選択できる
    * JankStats
      * API level 16まで対応
      * Identify
        * 実デバイスからフレームデータを取得
      * Attribute
        * UIの状態やアクションを記録することでレポートにUIのコンテキストを追加できる
      * Report
        * フレーム毎に監視し、データを集計、アップロードし解析やデバッグを行う
      * 使い方
        * `Activity#onCreate`で`JankStats.createAndTrack`
          * 頻繁に呼び出されるので可能な限り軽量にする
        * UIのコンテキストを追加するには、`addStates`でkey,valueを指定する
    * 開発者向けドキュメントが更新されパフォーマンスに関して1箇所で確認できるようになる
* Android Framework improvements
  * Mainlining ART
    * Android 12以上から通常のAndroidのリリースサイクルとは別にARTが更新される
    * 利点
      * OpenJDK API
      * Performance updates
      * Bug fixes
  * The new Garbage Collector
    * Androidの制約
      * Battery
      * Framerate
      * Memory
    * 必要なGCの特性
      * Allocation
      * Concurrency
      * Compaction
    * `Concurrent Copying`
      * なぜ必要だったのか？
        * オブジェクト毎の読み込みで固定なオーバーヘッドがあった
        * GCが走らないタイミングでもそれらは発生している
        * Code size
          * コンパイルされたコードに含まれるのでストレージ、RAM、キャッシュなどの負荷になっていた
        * Execution time
          * 条件分岐も含めオブジェクトの読み込み毎に実行される
      * Compaction via Copying
        * `RSS cliff`
           * GCの開始よりも終了直前のメモリ量が増えている
          * Userfaultfd
            * Linux kernel feature
      * 利点
        * 固定のオーバーヘッドがなくなり、コードサイズが10%程度削減
        * RSS cliffがなkなる
        * Efficient GC algo
          * Atomic ops O(#pages) vs O(#refs)
          * h/w prefetch friendly
          * Maintains allocation locality
    * Runtime improvements
      * Faster JNI Calls
        * 2.5倍以上早くなる
      * Faster Reference Processing
        * Jankの懸念がなくなる
        * `Reference.refersTo()`がpublicに
      * Faster Interpreter
        * クラス、メソッドの検索の改善
      * More install-time Verification
        * 実行時の検証を避ける
  * ART Summary
    * Lower memory use
    * Faster runtime
    * Updatable across releases
