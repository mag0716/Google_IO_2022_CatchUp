# [Common performance gotchas in Jetpack Compose](https://io.google/2022/program/213421b6-9873-464f-9b36-38eeb232a854/)

* Configuration
  * Jetpack Composeでのパフォーマンスをテストする場合は難読化した状態で行うことが重要
* Gotchas
  * Something to remember
    * `LazyColumn`の`items`の引数でデータのソートを行う
      * recompositionの度にソートが行われてしまう
      * -> コストが高い処理を1度だけ実行するために`remember`を利用する
  * A key piece
    * `LazyColumn`の`items`にkeyを渡していない
      * デフォルトだとindexが利用されるが、アイテムの移動や削除が発生するとrecomposeされてしまう
      * -> keyにアイテムごとのユニークな値を指定する
      * 詳細は`Lazy layouts in Compose`で
  * Deriving change
    * リストのスクロールされたらボタンを表示する処理に`ListState`を利用する
      * `ListState`はフレームごと、スクロールの度に変化するので必要のないrecompositionが発生する
      * -> `derivedStateOf`を利用し変化の頻度を吸収する
      * 毎回生成が必要なデータに対して`derivedStateOf`を利用するのはNG
  * Procrastination
    * `animateColorBetween`の色を`Box`の`background`に指定する
      * Drawだけ実行したいのにComposition, Layoutが毎フレーム発生してしまう
      * -> `background`ではなく、`drawBehind`を利用し背景色を描画することで必要になるまでStateの読み込みを先延ばしする
  * Running backwards
    * すでに読み込まれたStateを書き換える
      * 毎フレームrecompositionが発生してしまう
      * -> ViewModelで計算した結果をそれを読み取るだけにする
  * Covering your bases
    * リリースモードで確認しているがカクツキが起こる
    * -> Baseline Profilesで解析する
      * Baseline profilesはAndroid Studioから実行している時は利用できない
      * -> Macrobenchmark
    * リソース
      * goo.gle/baseline-profiles
      * goo.gle/baseline-profiles-codelab
