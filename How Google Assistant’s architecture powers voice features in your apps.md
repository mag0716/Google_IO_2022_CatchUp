# [How Google Assistant’s architecture powers voice features in your apps](https://io.google/2022/program/23a82db5-cbd2-45f0-bc9e-2aa1cec254c5/)

* Assistant's Architecture Components
  * ユーザーの音声コマンドをGoogle Assistantが受け取り、自然言語解析(NLU)を用いて合致するIntentとパラメータの抽出を行い該当するアプリを起動する
* Speech Recognition
  * 音声を解析しテキストに変換する
  * Natural Language Understanding(NLU)
    * Intentとパラメータを生成
    * Yesにも多くのバリエーションがある
      * Google Assistantは違ったバリエーションのインプットを理解することができる
    * `book a table for four at Bill's Restaurant for tomorrow night at 8.`
      * four = 人数, 8 = 時間として理解することができる
    * Google Assistantは文脈を理解することもできる
      * `How is the weather in Mountain View?`の後に`How about New York?`とすると天気についての話だと理解できる
    * Google Assistantとの対話
      * `book a table for four at Bill's Restaurant`のようにいつかを指定しなかったらGoogle Assistantは`When do you want the table?`などと返す
      * それに対して`Tomorrow night at 8`と話すとリクエストに必要な情報が集まることになる
  * How Devs can Plug in
    * **Android app developer -> App Actions**
      * Built-in Intents(BII)
        * Googleが必要な言語モデルを管理するので開発者は何もしなくて良い
      * 実装方法
        * shortcuts.xmlに`capability`を定義
          * 該当するBIIを指定
          * アプリが該当するクラスとパラメータを指定する
        * `shourtcut`を定義
        * string-arrayで特定のパラメータの同義語を定義できる
          * Google Play Consoleにアップデートすると、Assistantに取り込まれる
      * 新機能
        * Brandless Queries
          * 明示的にアプリ名を指定しないリクエストでもアプリが動作する
        * App Installs Suggestions
          * アプリがインストールされていない場合、インストールのためのページをGoogle Assistantで表示する
        * Smarter Custom Intents
          * 多くのパターンのモデルを用意しなくてもよくなる
        * WearOS and Auto Support
    * Innovator in the conversational space -> Conversational Actions
    * Hardware developer -> Smart home SDK
