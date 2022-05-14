# [What's new in Android media](https://io.google/2022/program/f6863994-eab8-489f-8d62-82c8a9c486ab/)

* New Platform capabilities
  * Android 13からの変更点
    * HDR Video
      * Capture/Encode
      * Playback
      * Edit
      * Share
      * レンダリングにはSurfaceViewが必須
        * TextureViewを使っているのであれば移行が必要になる
      * Media3を利用するとHDRのサポートが容易になる
      * HDR10
        * 再生に必須
      * HLG10
        * 撮影、再生に必須
      * Dolby, HDR10+はOEMによって有効になる
  * Spatial Audio
    * 「空間オーディオ」：映画館のように全方向から聞こえる
    * 頭のトラッキングによってstatic, dynamicに関わらずサポートされる
    * `Spatializer`
      * デバイスがサポートしているかを確認してから利用するオーディオを切り替える
    * ExoPlayer 2.17で試すことができる
      * Android 12L以上でデフォルトで有効になっている
  * MIDI 2.0をサポート
    * 1.0からの改善
      * resolutionが7 -> 32bitへ
      * non-Western annotationsをサポート
* Media3 & ExoPlayer
  * ExoPlayerからの移行
    * com.google.android.exoplayer2 -> androidx.media3
      * exoplayer-core -> media3-exoplayer
      * exoplayer-ui -> media3-ui
      * extension-cast -> media3-cast
  * ExoPlayerとMedia3は並行してリリースされる
    * Media3は今年stableがリリースされる
  * ExoPlayerの新機能
    * 2.14
      * DRM keyのプリフェッチ
        * よりシームレスにコンテンツのバッファリングが可能になる
    * 2.16
      * Android 12互換
        * ダウンロード処理周りの更新
    * 2.17
      * サーバーサイドでの広告の挿入
* Performance Class
  * Jetpack Core Performance Library
    * Android 12以上のデバイスでは `MEDIA_PERFORMANCE_CLASS` が利用される
    * Android 11以下のデバイスでは手動テストかCTS(Compatibility Test Suite)のテスト結果が利用される
    * 利用方法
      * `Application#onCreate`で`DevicePerformance.create`を呼び出す
      * `mediaPerformanceClass`から動画の解像度を求める
  * 更新点
    * メモリの要件が増大
    * Media
      * Round trip audio latency
      * Wired headsets & USB audio devices
    * Camera
  * AV1
    * Netflix
    * Google Duo
