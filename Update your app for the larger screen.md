# [Update your app for the larger screen](https://io.google/2022/program/eb6e6fb3-b24d-4baf-a1d9-f176198fc595/)

* Quality matters
  * Material guidelines
  * App quality guidelines
  * Compatibility checklist
* Android 12L
  * タスクバーが改善され、Multi-windowがデフォルトになった
  * Compatibility mode
    * 端末の向きがそのままアプリの向きになるとは限らない
  * Input support
    * キーボード、マウス、スタイラスペン
* Developer resources
  * 大画面対応を楽にするライブラリ
    * Jetpack WindowManager
    * Window size classes
    * Activity embedding
    * SlidingPaneLayout
    * NavigationRail
    * Jetpack DragAndDrop
    * Jetpack CameraX
  * ツール
    * Resizable emulator
* Jetpack WindowManager
  * `maxWindowMetrics`, `currentWindowMetrics`
  * 既存のAPIの難しさを軽減することが目的
  * `Activity#onCreate`でサイズを取得することができる
* Window Size Classes
  * Compact, Medium, Expanded
* Activity Embedding
  * 1Activityが推奨だが、既存コードで大画面対応に対応するための方法として提供
    * 画面サイズによって何を表示するかをハンドリングする必要がない
  * 詳細は goo.gle/activity-embedding
* SlidingPaneLayout
  * 画面サイズによってsingle or dualを切り替える
* NavigationRail
  * サンプル：goo.gle/Trackr
* Drag and drop
  * beta
    * goo.gle/jetpack-drag-drop
  * `DragStartHelper`
  * `DropHelper`
  * リソース
    * https://goo.gle/drag-drop
    * https://goo.gle/drag-drop-sample
* Camera layouts
  * デバイスの向きとディスプレイに表示するプレビューの向きが密接に関係している
    * Compatibility Modeではデバイスの向きとアプリの表示向きが異なる
    * Camera orientation
      * センサーは画面の長辺に合わせる
      * センサーと画面の角度が自然な向きとなる
      * 通常スマホだと90度
      * API 32以降はstatic fieldでなくなる
        * `CameraCharacteristics`から取得可能
    * Device rotation
      * 自然な向きで相対的に定義されている
      * 画面上に描画されたグラッフィックの回転を示す
      * 通常縦向きのスマホだと0
      * `Display.getRotation()*90`で求められる
  * Aspect Ratio
    * goo.gle/codelab-camera2
  * Jetpack CameraX
    * 自動的にディプレイに必要なプレビューに変化する
* Testing
  * Resizable Emulator
  * Desktop Emulator
    * ChromeOSなどのデバイスでテストするためのネイティブなデスクトップ環境を用意することが目的
