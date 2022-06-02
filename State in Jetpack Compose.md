# [State in Jetpack Compose](https://io.google/2022/program/c9768969-9e81-4865-9dff-29a2ab1201ea/)

* [Codelab](https://developer.android.com/codelabs/jetpack-compose-state#0)
  * Key Concept
    * Composition：Composableを実行する際に構築するUIの説明
    * Recomposition：データ変化時にCompositionの更新するために再実行
    * Compose's state tracking system：特定の状態を読み込んでいるComposableのためにRecompositionをスケジュールする
    * stateful：状態を保持するComposable
    * stateless：状態を保持しないComposable
    * State hoisting：状態を呼び出し側に移動することでstatelessにする実装パターン
  * LazyColumnのitemでスクロールで状態が破棄されないように`rememberSaveable`が利用できる
