# [Input for all screens](https://io.google/2022/program/a55aec14-5bda-47e0-b259-7a1f7bb366b8/)

* Jetpack Compose 1.2からマウスなどのスクロールをサポートした
* 単純なミスはキーボードやマウスでテストしていないこと
  * スマホでも物理デバイスを利用することはできる
  * ソフトウェアキーボードが必ず表示されるという前提でレイアウトしていると物理キーボードを利用する際に不要なスペースが生まれてしまう
* テキスト選択  
  * `textIsSelectable`
  * `SelectionContainer`
* キーボード
  * shortcuts
    * Android ViewsもJetpack Composeもサポートしている
    * `dispatchKeyShortcutEvent` でオーバーライドできる
    * Jetpack Composeの場合や`onPreviewKeyEvent` modifierが用意されている
  * navigation
    * tabや矢印キーでの移動
    * ユーザが必要とする要素全てに移動できるか？
    * 正しい順番で移動できるか？
    * 移動が効果的か？
    * 移動先をカスタムする
      * Android Views：`nextFocusForward`
      * Jetpack Compose：`FocusRequester`
    * 不要な要素に移動しないようにする
      * Android Views：`focusable=false`
      * Jetpack Compose: `focusProperties { canFocus = false }`
    * ネストしている子供の要素に移動しないようにする
      * Android Views：`screenRenderFocusable`
* マウス
  * Hover States
    * Android Views：`setOnHoverListener`
    * Jetpack Compose：`Modifier.clickable`でホバーした状態が追加される
      * クリックなしの場合は、`hoverable`に`InteractionSource`を渡す
* スタイラス
  * github/chromeos/low-latency-stylus
* リソース
  * goo.gle/input-design-guidelines
  * goo.gle/large-screen-quality
  * chromeos.dev/en/android
