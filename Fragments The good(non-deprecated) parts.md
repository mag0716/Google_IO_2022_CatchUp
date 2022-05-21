# [Fragments: The good(non-depreacated) parts](https://io.google/2022/program/c9085b18-4e8e-4183-b303-1d1716b0c070/)

* Good Fragments APIs
  * androidx.fragmentではなくフラグメントがアクセスできるようになった他のコンポーネントを利用する必要がある
    * AndroidX Lifecycle
      * ViewPager, ViewPager2では現在のFragmentのみRESUMEDとなる
    * ViewModel
      * App UI LayerのUI elementsはFragmentに所属している
      * State holdersはUIの状態を管理し、ViewModelが利用される
        * ViewModelを共有させたい
          * 親のFragment：`ownerProducerにparentFragmentを渡す``
          * Activity：`activityViewModels()`
          * Navigation Graph：`navGraphViewModels()`
    * Fragment Results
      * 特定のFragmentにデータを受け渡ししたいケースで利用する
      * FragmentManagerが利用される
      * `scenario.onFragment`で結果を指定することでテストも容易
* Testing Fragments
  * FragmentFactory
  * 何をテストするのか？
    * コントロールしないものにどれだけ依存しているのか？
      * Activityの遷移はActivityManagerが行なっておりコントロールできない部分なのでテスト対象としない
      * ActivityResultRegistryのようなコンポーネントがあればテストが容易になる
        * コンストラクタインジェクションを利用する
  * Menus and the AppBar
    * テストを容易にする方法は2種類
      * FragmentがToolbarを所有する
      * FragmentがActionBarにメニューを追加する
        * `requireActivity()`で`MenuHost`を取得し操作する
        * lifecycle awareになる利点がある
        * MenuProviderは今までの`onCreateMenu`, `onMenuItemSelected`と同等のインタフェースとなるので理解しやすい
* old ways
  * deprecated
  * 互換性のため維持されているのでFragmentのバージョンを更新してもアプリが壊れることはない
* Migration
  * コンパイル時のLintで指摘してくれる
  * FragmentStrictModeで実行時に検証する
    * `allowViolation`で特定のクラスを除外することができる
