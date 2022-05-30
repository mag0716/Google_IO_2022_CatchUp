# [Learn how to enable shared experiences across platforms](https://io.google/2022/program/5b2df2ff-fc08-4a61-89e7-88731938b010/)

* Google Meetのlive sharing
  * State sync API
    * 参加者全員のデバイスでアプリのコンテンツの制御を同期させるAPI
      * 誰かがコンテンツを停止されたら全ての参加者のコンテンツも停止する
      * 誰かが新しく共有したら全員が同じコンテンツをみる
  * Picture-in-Picture
    * 同期したアプリのコンテンツ同じViewにMeetを同時に表示することができる
  * Chromecastにも対応している
* Starting the experience
  * エントリーポイント
    * Meetから共有するActivityを開始する
      * Activityの一覧が表示される
    * Meet中にアプリから開始する
    * アプリからActivityを開始する
* 対応アプリ
  * Youtube
  * Spotify
  * Heads Up!
  * UNO!
  * Kahoot!
* SDKは今年リリースされる
* Youtubeの対応例
  * プレミアムアカウントが必要
    * 開始するのがプレミアムアカウントのユーザーであれば他の人はアカウントなしでOK
  * シェアメニューからLive sharingができる
  * 実装方法
    * LiveSharingClient
    * MeetingStateHander
    * CoWatchingController
    * CoWatching
* Early Access Sign up
  * https://goo.gle/livesharing-eap
