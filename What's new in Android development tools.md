# [What's new in Android development tools](https://io.google/2022/program/8215c766-f097-4b18-bc97-5085d77c4dad/)

* Roadmap
  * Bumblebee
    * Device Manager
    * Animated Vector Drawable Preview
    * ADB over Wi-FI
  * Chipmuck
    * Compose Animation Preview
    * Jank Detection
    * 品質向上にフォーカスしていたので新機能は少なめ
* Demo
  * Dolphin, Electric Eel
    * 特定のAGPのバージョンへの移行が容易
    * Jetfier Check
      * 安全に利用するためにバージョンアップが必要なSDKを特定できる
    * Configuration cache
      * 新規プロジェクト作成時の設定のままでビルド速度に影響を与えている設定の特定
      * org.gradle.unsafe.configration-cache
    * `./gradlew lint | grep lint`
      * 影響のあるタスクだけ実行される
      * CIでのLint実行速度を改善してくれる
    * `devices`
      * テスト用のデバイスを定義できる
      * CPUはテストを実行しているPCから自動で選択してくれる
      * GitHub Actionsでもgradleコマンドを実行するだけでテストが可能
    * APK Analyzer
      * assets/dexopt/baseline.prof
        * release variantsのみ
    * デバッグでのパフォーマンス解析
      * Profiler
    * Jank Profiling
      * Display -> Janky frames
    * Logcat
      * 色分けされて見やすくなった
      * Show repeat tag
        * 連続するタグのログの場合はタグを省略してくれる
      * package:mine
        * 自分のアプリのみフィルタリング
    * Device Manager
      * EmulatorがIDE上で表示される
      * 物理デバイスもIDE上で表示できるようになる
        * ADB wirelessを利用して接続しているデバイスも選択できる
        * API level 26以上
      * Wear OSのEmulatorを物理デバイス、Emulatorのどちらでもペアリングすることができる
      * Bluetoothのサポート
        * 心拍数のダミーデータをターミナルから生成することができる
      * Resizable Emulator
        * 複数のEmulatorを利用するより短時間で複数画面サイズのデバイスでの確認ができる
      * Visual Lint
        * layout editor内に表示される
        * 複数の画面サイズの表示が1画面で確認できる
        * Issue Panelに問題がある箇所が指摘される
      * Live Edit
        * いままでPreviewだけだったが起動中のデバイスやEmulatorに対しても文字列やパディングの変更が即座に反映されるようになる
        * Buttonなどの追加も反映される
        * Resizable Emulatorと併用して利用すると、複数画面サイズの対応も簡単
        * 不正な値などを入れるとアプリがクラッシュする
      * Compose Preview
        * 複数の設定をAnnotationでまとめられ、複数箇所で利用できる
        * Compose Previewの利点はテーマなど切り替えの手間がかかるものについての確認が容易な点
          * Live Editと組み合わせて利用するのがよい
        * shaderを使ったアニメーションもPreview上で確認できる
      * Recomposition Count
        * recompositionの回数を確認できる
      * Firebase
        * IDE上でアカウントにログインすると、Crashlyticsでの指摘がIDE上でも表示できるようになる
        * App Insightウィンドウで一覧が確認できる
* Updates
  * `android.enableJetifier`を削除すると10%程度ビルド速度が改善される
  * Baseline Profilesを利用するとアプリの起動速度が改善される可能性がある
