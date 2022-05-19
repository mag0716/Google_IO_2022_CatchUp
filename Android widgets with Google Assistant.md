# [Android widgets with Google Assistant](https://io.google/2022/program/0d911b1f-b810-49c8-a710-6d8c411b5147/)

* Workshopの概要
  * https://codelabs.developers.google.com/codelabs/appactions-widgets#0
    * Widgetを実装済みのエクササイズアプリでGoogle Assistantと連携し最新のエクササイズ結果をGoogle AssistantのUI上とTTSを利用してユーザーに通知するように変更する
    * App ActionsのテストをするためのPlugin
      * Android Studio上からApp Actionsのコマンドを発行することができる
    * App Actions Widgets Extension Library
      * WidgetをGoogle AssistantUI上に表示するために必要
        * `com.google.assistant.appactions.widgets.PIN_APP_WIDGET`
      * TTSのサポートにも利用されている
        * AppActionsWidgetExtension生成時に`setResponseSpeech`でTTSに渡す文字列をセットする
    * BIIのパラメータを見て、パラメータがあれば指定の種類の情報を取得するように変更する
    * データ取得後に、BIIがあればTTSを追加する
