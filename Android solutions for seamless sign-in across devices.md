# [Android solutions for seamless sign-in across devices](https://io.google/2022/program/c4be021c-53ec-493e-a3c1-7db7a168317e/)

* ユーザーは多くのデバイスを利用している
  * アメリカの一般的な世帯は2019年は11台、2021年は25台接続している
* 新しいデバイスを設定するのは大変
  * 数多くのアプリでサインインする必要がある
* 解決策
  * Block Store
    * タッチなしでのサインイン
    * セキュアで暗号化されたストレージを提供する
      * デバイスのGoogleアカウントからユーザーを識別する
    * アプリを初めて起動した時にすでにサインインしている
      * 同意のためのダイアログは表示されない
    * 実装が簡単
      * 30行程度
      * 開発者はデータやユーザー体験をコントロールすることができる
    * デバイス間のリストア、クラウド経由でのリストアのどちらもサポートしている
      * 将来的には異なるフォームファクターでもリストアできるようにする
    * フロー
      * 現在のデバイス
        * アプリでサインイン
        * トークンは暗号化されデバイス上に保存される
        * (オプション)クラウドバックアップが有効であればクラウド上にも保存される
      * 新しいデバイス
        * 新しいデバイスでリストアを行う
        * 新しいデバイスでアプリとBlock Storeのデータが取得される
        * アプリはBlock Storeトークンをリクエストし、復号されたトークンがアプリに返される
        * アプリでサインインされた状態となっている
    * 実装方法
      * `com.google.android.gms:play-services-auth-blockstore:16.1.0`
      * ログイン成功時に、`storeBytes`でトークンを保存する
      * 取得時は`retriveBytes`
      * クラウド上に保存する際は`setShouldBackupToCloud`
        * Android 8以上はロックスクリーン以降でしか読み取れないので、Googleから保存したトークンを読み取ることはできない
      * E2Eでの暗号化が有効かどうかをチェックするには`isEndToEndEncryptionAvailable`を利用する
    * developers.google.com/blockstore
  * OneTap
    * Googleアカウントと統合されサインアップとサインインのワークフローが統一されている
    * Sign up
      * Googleアカウントが必要
    * Sign in
      * Googleアカウントとパスワード認証のどちらもサポート
    * developers.google.com/identity/one-tap/android
  * Passkeys
    * FIDOが利用され、デバイス間でパスワードなしでセキュア
      * FIDOはAndroid, Chrome以外でも広く利用されているもの
    * Android上で生成されバックアップされ、同じGoogleアカウントでサインインできる
    * フロー
      * サインイン後にPasskeysを利用するかのダイアログが表示される
      * システムのダイアログが表示される
      * デバイスと生体認証が利用され1ステップで2要素認証が提供される
      * PCで利用する際はQRコードをスマホで読み取り、スマホでアカウントを選択することでPC側でもサインインされる
        * Bluetoothを利用している
        * ネイティブアプリでも同じ流れで利用することができる
    * developers.google.com/identity/fido
    * 今年開発者向けにテスト方法が提供される
