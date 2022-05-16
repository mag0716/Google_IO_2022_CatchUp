# [What's new in Google Play](https://io.google/2022/program/e1fe8007-7338-4e33-814b-ecbfcb706c5e/)

* Privacy & security
  * Google Play SDK Console
    * サードパーティのSDKに問題があると通知される
    * SDKの提供者はGoogleに対して通知することでSDKを利用しているアプリ開発者にGoogle Play Consoleを通じて通知される
      * アプリリリース前に気づくことができる
    * 80以上のSDKがすでに登録されている
  * Google Play SDK Index
    * それぞれのSDKの詳細やSDKが導入されたアプリのインストール数などが確認できる
      * どれを利用するのかを決定する材料にできる
  * Play App Signing + Cloud Key Management
    * Play App SigningがGoogle Cloud Key Managementを利用するようになる
    * key rotation
      * Play Consoleでkeyの変更ができるようになる
  * Play Integrity API
    * 海賊版の検知ができるようになる
    * Truecaller, Wooga, GameInsightなどですでに利用されている
  * Data safety section
    * 全ての開発者は送信する必要がある
      * 2022/7/20までに完了させる必要がある
    * 承認されていない場合、新しいアプリの送信やアップデートが拒否される可能性がある
  * Privacy Sandbox on Android
    * 端末固有のIDを利用しなくて良くなる
* App quality
  * Android vitals
    * Google Play Developer Reporting API
      * Google Play Console外の計測結果を統合することができる
        * 例．Crashlytics
    * country filters
      * 地域、国でフィルタリングできる
        * 優先で直すべき問題を特定できる
  * Reach & devices
    * 収益が多いデバイスを特定できる
  * Device catalog
    * アプリでもっとも重要なデバイスを特定できる
  * Test tracks for form factors
    * テスト状態をそれぞれで指定することができる
    * Android Automotiveに対応
    * WearOSはもうすぐ対応
  * In-app updates API
    * 24時間かかっていたのを15分で更新を検知できるようになった
* Business success
  * Custom store listing
    * deep linksを利用する
    * 例．ハロウィンなどのイベント時に専用のスクショを見せるようにする
    * 50以上用意することができる
  * Store listing experiments
  * Deep links
    * Deep linksに関する情報を1ページでまとめて表示できるようになる
  * LiveOps(beta)
    * Activeユーザーと収益が多いアプリが表示される
    * Offers
    * LiveOps deep links
    * Reporting
  * Google Play Commerce
    * Merpay
    * Ultra-low price points
      * 1ドル以下の少額を設定できるようになる
    * Subscriptions
      * Subscriptionごとに複数のOfferを設定することができるようになる
        * Base plan
          * 例. 1ヶ月更新、1年更新、1ヶ月のプリペイド
      * Eligibility
      * Pricing
        * 地域毎の価格
        * 価格の更新(既に課金しているユーザーには影響しない)
        * プリペイド
    * In-app messaging
      * Play Billing Library 5.0での機能
      * 課金しているユーザーの離脱を防ぐ
      * 更新タイミングの通知
      * early testではメッセージがあると課金の継続をしてくれる頻度が2倍になる
* `Power your success with new acquisition, engagement and monetization tools`
