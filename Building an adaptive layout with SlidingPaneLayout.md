# [Building an adaptive layout with SlidingPaneLayout](https://io.google/2022/program/95d82d1b-8cfe-4617-a9da-5806c72a4284/)

* 一覧、詳細画面があるアプリを`SlidingPaneLayout`を使って改善する
  * 一覧画面の`Fragment`のレイアウト
    * rootを`SlidngPaneLayout`に置き換え
    * 詳細画面の`Fragment`を配置するために`FragmentContainerView`を配置
  * 一覧画面の`Fragment`
    * 画面遷移処理の代わりに`SlidingPaneLayout#openPane()`を呼び出す
      * スマホだとアニメーションありで詳細画面が開くようになる
    * バックキータップで`SlidingPaneLayout#closePane()`を呼び出す
    * スワイプジェスチャーでの開閉をさせたくない場合は、`SlindingPaneLayout#lockMode`を指定する
