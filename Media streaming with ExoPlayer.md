# [Media streaming with ExoPlayer](https://io.google/2022/program/11094c8f-f7c5-42a6-9e8f-df94e83f5d27/)

* https://developer.android.com/codelabs/exoplayer-intro#0
  * Media3を利用して音楽、動画のストリーミング再生を行うアプリ
    * 利用するモジュールは `media3-exoplayer`, `media3-ui`, `media3-exoplayer-dash`
    * UIには`PlayerView`を利用
    * マルチウィンドウを考慮した初期化、後処理の呼び出しタイミング
    * 単一のメディアファイルで実装した後に複数のメディアファイルの実装を行う
      * `ExoPlayer#addMediaItem`で追加しているだけ
    * ストリーミング再生
      * `DefaultTrackSelector`
      * `MediaItem`生成時にMimeTypeを指定
        * Codelabでは`APPLICATION_MPD`を利用
    * 再生状態の検知
      * `Player.Listener#onPlaybackStateChagned`
      * 再生中かどうかを検知したい場合は `onIsPlayingChanged`
      * 動画の1フレーム目が描画されたタイミングを検知：`onRenderedFirstFrame`
        * 再生までどのくらいかかったのかを計算するのに役立つ
      * 全てのイベントを検知：`onEvents`
        * 再生状態によってUIを変化させる
        * メディア切り替え後に特定の再生位置から再生する
