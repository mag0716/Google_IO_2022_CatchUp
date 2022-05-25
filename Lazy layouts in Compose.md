# [Lazy layouts in Compose](https://io.google/2022/program/14bb63ef-2dd1-460a-9871-5f51ec1afec9/)

* 左右にpaddingを持たせたいがスクロール時にはクリッピングして欲しくない
  * `contentPadding`
* アイテム間のマージンを追加したい
  * `horizontalArrangement`に`spaceBy`
* スクロール位置の保存やスクロール状態へのアクセス
  * `rememberLazyListState()`
  * `firstVisibleItemIndex`, `firstVisibleItemScrollOffset`
    * スクロールしたらボタンを表示したい
      * 余計なrecompositionを発生させないために`derivedStateOf`でラップことで計算結果が変化した時のみrecompositionが発生するように対応する必要がある
    * 表示されているアイテム内の動画を再生したい
    * ボタンタップでスクロール位置をトップに戻したい
      * `scrollToItem`, `animateScrollToItem`
        * 上記はsuspend funなので`rememberCoroutineScope`で取得したCoroutineScopeを利用する必要がある
* Lazy grids
  * 1.2でstableになる
  * GridCells.Fixed：固定のセル数
  * GridCells.Adaptive：指定したサイズのセルが画面サイズによって動的にセル数が決定される
  * `calculateCrossAxisCellSizes`
    * セルによってサイズを変えることができる
  * `span`
    * 特定の行、列のセルのサイズを変更する
* experimental API
  * Custom lazy layouts
    * ScallingLazyColumn
      * Wear OSで利用している
    * Staggered grids
      * まだ有効ではない
  * Item animations
    * LazyGrid でもアイテムの位置変更でのアニメーションをサポート
      * `Modifier.animateItemPlacment()`
        * `tween`でアニメーション速度をカスタムすることができる
    * 追加、削除時のアニメーションはWIP
* Tips
  * 0pxのアイテムは利用するな
    * 全てのアイテムがレイアウトされてしまい、表示されていないアイテムも生成されてしまう
    * -> デフォルトサイズを指定しおく。データの取得前後でアイテムのサイズが同じなのはよいプラクティス
  * 同じ方向にスクロールするコンテンツをネストさせない
    * View Systemでは可能だったがパフォーマンスに影響していた。Jetpack Composeでは実行時例外になる。
      * 固定サイズであれば可能
    * -> `LazyColumn`, `LazyRow`だけで実現する
  * 1つのアイテムに複数要素の配置は注意
    * 1要素のデータが変化した時でも他の要素もrecompositionが発生してしまう
    * indexがずれる
    * dividerであれば影響は少ないので問題はない
  * custom arrangementsの利用を検討する
    * 例．アイテム数が少ない時もフッターを画面の一番下に表示する
      * `Arrangement.Vertical`を継承したクラスを用意
* Performance
  * R8を有効にした状態で動作確認する
    * Baseline Profileによって初回起動後のパフォーマンスが改善する
  * Reusing
    * スクロールによって新たに表示されたアイテムは再利用されて表示される
    * 1.2から`contentType`を指定できるようになり、再利用が効率的になる
  * Prefetching
    * 前のフレームでCompose, Measureを行なっておくことで、描画がフレーム内に収まるようにする
