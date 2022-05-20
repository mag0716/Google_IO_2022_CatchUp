# [Back to the basics of System Back](https://io.google/2022/program/5c6a8dbb-7ac2-4c31-a707-0a16e8424970/)

* What we had before
  * Androidの初期から物理ボタンが存在していた
  * 物理ボタンからジェスチャーナビゲーションに進化
  * これから2年で戻るボタンのエクスペリエンスが改善される
* Unpredictable Back
  * スワイプ操作で誤ってアプリが終了してしまうことがある
* Predictable Back
  * 遷移のプレビューをユーザーに表示する
  * この変化によってユーザーは操作を継続するかどうかを選択できるようになる
* The new platform API
  * `OnBackInvokedCallback`
    * `onBackPressed`の代わりに`onBackInvoked`が呼ばれるようになる
* Migrate
  * Android 13では明示的にオプトインする必要がある
    * `enableOnBackInvokedCallback`
    * オプトインしていないと何も影響しない
  * Android 14からはこの機能がデフォルトで有効になる
  * androidx.activity:activity:1.6.0
    * 導入することで後方互換性を考慮した上でサポートできる
      * `onBackPressed`を自動的に呼び出す
    * Tied to component
      * コンポーネントの生成時にコールバックが追加される
      * `isEnabled`によって有効状態を切り替えられる
    * Temporary overlays
      * コンポーネントを有効にするまでコールバックの追加を待機できる
      * 常に最後に追加されるのでデフォルトの順番から変更することができる
    * Stack Ordering
      * 最後に追加したコールバックが最初に処理される
  * 新しいAPIを使えないケース
    * onKeyDown, onKeyUpを使っているようなDrawerLayout
      * DrawerLayoutの開閉状態によってコールバックを登録するかどうかを決定する
* The long term plan
  * Jetpack Compose, FragmentNavigationのアプリ内の遷移には対応できていない
    * デザイナー、開発者、ユーザーと議論が開始されている
* More resources
  * https://codelabs.developers.google.com/handling-gesture-back-navigation?authuser=1#0
