# Simple Media Downloader v2.0.0

公開日: 2026-11-23（JST）

**配布ファイル:** `Simple.Media.Downloader_2.0.0_x64-setup.exe`（107835232 bytes / SHA256 `fa83d941117b64044d3039eae497523e33f3b1e5e5888b4ac73a1016cb9fe09b`）

## 主な変更

### 日本語・英語の表示切り替え

- 右上の設定メニューから日本語／英語を切り替えられます。変更はすぐ反映され、再起動後も保持されます。
- 画面、通知、使い方、代表的なエラーの案内に対応しました。表示言語を変えても音声の選択や保存設定は維持します。

### ライブ録画と予約

- ライブURLと形式・画質を確認する入口と、録画状況の画面を整理しました。
- YouTubeの開始待ちとTwitchのオンライン待ちを予約できます。予約待ちや録画中の状態を確認しやすくしました。
- Twitchライブの画質は、選べる候補の最上段を初期選択します。手動で選んだ画質はそのまま使います。

### プレイリストと画面の改善

- プレイリストの選択と保存操作、新着の選択バー、画面切り替えや項目の動きを改善しました。
- プレイリスト一覧は表示言語に合わせてタイトルを取得します。ホームのタイトルと保存名は従来の方針を維持します。
- 音声トラックのないX投稿動画のMP4保存と、日本語・絵文字を含む長い保存名の扱いを改善しました。

### ライセンスと案内

- BOOTHの正式キーと72時間の仮コードの入力に対応しました。仮コードは提供元から案内された場合に利用してください。販売開始・商品公開の案内は別途行います。
- 本体更新の取得先をWebサイトの案内へ整理し、問い合わせの主窓口を[X @legion_edge](https://x.com/legion_edge)にしました。

## 部品更新

2.0.0対応の部品構成 `win-x64-20261123-1` を公開しました。1.2.1／1.3.0／1.4.0／1.5.0の互換性と、同梱するyt-dlp・Deno・FFmpeg／ffprobeの版を維持しています。

公式サイトのダウンロードボタンは現在v1.5.0を案内しています。v2.0.0は[GitHub Releaseのinstaller](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v2.0.0/Simple.Media.Downloader_2.0.0_x64-setup.exe)から取得してください。公式サイトの配布欄の更新は別途行います。

## 導入・更新

1. 実行中のSimple Media Downloaderを終了します。
2. `Simple.Media.Downloader_2.0.0_x64-setup.exe`を実行します。
3. 管理者確認の後、Program Filesへ全ユーザー向けに導入されます。
4. 「更新と修復」で本体版と部品の状態を確認してください。

設定、履歴、購入ライセンスの保護データ、保存済み媒体は保持する設計です。

## 注意事項

- Windows 11 x64専用です。Windowsコード署名はありません。公開ページのSHA256を確認してください。
- WebView2 Runtimeがない環境では、導入時にMicrosoftのbootstrapperを取得します。
- Free機能の利用に購入ライセンスは不要です。Pro機能には有効な購入ライセンスが必要です。
- 対象サービスの変更、公開状態、認証・アクセス確認などにより保存できない場合があります。
- この版のclean Windowsでの導入・起動、正式installerからの公開HTTPS部品適用、実BOOTH注文からの認証は未確認です。

Webマニュアル: [Simple Media Downloader](https://legion-edge.dev/smd/manual/)

作成元commit: `30d7137d786488972e00af5995c44b9fb23ab3c5`。Windows nativeでfrontend1,055件（既存skip 1）、型検査、Rust関連12件、DebugBuild、試験鍵／localhostの部品適用・復旧11ケース、通常release／NSIS生成と展開物のhash照合を確認しました。
