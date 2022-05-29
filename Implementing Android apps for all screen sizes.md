# [Implementing Android apps for all screen sizes](https://io.google/2022/program/1351e983-465f-4b32-99e0-de0647240352/)

* セッション概要
  * スマホ、タブレット、PC、ChromeOSへの対応にフォーカス
  * Jetpack Composeでの実装
  * Now in Androidを例に説明
* Width
  * Compact：-600dp
  * Medium：600dp-840dp
  * Expanded：840dp-
* サイズの違いによって遷移が異なるのは推奨されない
  * 画面回転やFoldableでの開閉によってサイズがことなる遷移を維持できない
  * -> どの画面サイズでの遷移(Navigation Graph)は同じにする
* `rememberWidthSizeClass()`
* どの画面サイズでも同じデータを利用し表現方法を変える
  * Jetpack Composeだと従来のAndroid Viewに比べて簡単にUIの切り替えができる
* テスト
  * アーキテクチャに沿っていればViewModelのテストで画面サイズに依存する必要がない
  * `StateRestorationTester`
    * 画面回転や画面サイズの変化によるStateの保存、復元をテストできる
  * 引数で画面サイズを表す値を渡せるようにしておけば、それぞれの画面サイズのUIテストも容易になる
    * `TestExpandedWidth`アノテーションを指定しておけば、画面サイズが大きいテストのみを実行、除外することができる
