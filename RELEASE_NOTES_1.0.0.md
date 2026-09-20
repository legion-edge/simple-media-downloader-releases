# Simple Media Downloader v1.0.0 リリースノート

公開日：2026-09-20（JST）。無料版完成版v1.0.0を公開しました。[公式ダウンロードページ](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v1.0.0)から取得できます。

## 配布ファイル

| ファイル | サイズ（bytes） | SHA256 |
| --- | ---: | --- |
| [Simple.Media.Downloader_1.0.0_x64-setup.exe](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.0.0/Simple.Media.Downloader_1.0.0_x64-setup.exe) | 106118436 | `8eff5fa58af274e0d543ef6556749edddd1c10c29e3beffb9e1f106526d836b2` |
| [distribution-manifest.json](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.0.0/distribution-manifest.json) | 7739 | `084787ef97c5c1917185d2f3eaef7d6d15ff43a7274c9a69c3274847ab0448d4` |

manifestにあるビルド時の名前は`Simple Media Downloader_1.0.0_x64-setup.exe`です。公開asset名は空白をピリオドにした名前を使います。内容・サイズ・SHA256は同じです。manifestの`candidate-only`と作成日時はビルド時の記録として保持し、一般公開の実績はこの案内とReleaseに記載します。manifestのcommitは非公開本体のビルド元であり、公開repoのtag対象commitとは別です。

## 対象と利用条件

Windows 11 x64向け、日本語のYouTube通常動画・Shorts用ダウンローダーです。無料・認証不要で利用できます。変更していない公式配布バイナリは、APPLICATION-TERMS.txt、第三者告知とlicensesフォルダーを保持すれば転載・再配布できます。アプリ本体のソースは非公開で、OSSライセンスは付与していません。第三者ソフトウェアには各ライセンスが適用されます。v0.1.0の既存許諾は変更しません。

## v0.1.0からの改善

- 初回の保存先設定案内と、コンパクトな一覧・開始操作を改善しました。情報取得の開始間隔は最初の1件を除き最低3秒です。保存中は取得中ストリームの速度と推定残り時間を表示し、結合・変換中は処理名へ切り替えます。
- 一覧を1列／2列で選択して保持できます。狭い画面では選択を保持したまま1列へ戻ります。
- クリップボードからYouTube動画URLを入力欄へ取り込めます。初期値はOFFです。ONにした後の内容変更だけが対象で、情報取得や保存は自動で始めません。
- `{title}`、`{video_id}`、`{channel}`、`{upload_date}`を使うファイル名書式と、チャンネル別フォルダー保存に対応しました。初期値はタイトルだけ・フォルダーOFFです。条件は一覧追加時に固定し、同名時は連番で上書きを防ぎます。
- 「更新と修復」で本体版を表示し、利用者が選んだときだけ公式Releaseの新版を確認できます。本体の取得・インストールは手動です。部品更新とは別の機能です。
- 「問い合わせ」にXの主窓口とGitHub Issues、共有前に確認できる診断プレビューを追加しました。コピーは手動で、URL・保存先・ユーザー名・Cookie・生ログ・例外本文を含めず、自動送信しません。

MP4／MP3、複数URLの同時1件キュー、停止・再試行、最新100件の履歴、MP3の320／192／128kbpsと取得可能な画像・曲情報、部品更新・復旧は引き続き利用できます。

## v0.1.0から手動で更新する

1. 使用中のSimple Media Downloaderを終了します。公開済みv0.1.0には本体更新確認ボタンがないため、公式配布ページからv1.0.0のsetupを取得してください。
2. 公開ページと配布manifestのサイズ・SHA256を確認し、setupを実行します。現行Program Files版は旧版を残した状態から更新導入します。管理者権限が必要です。
3. 更新後は通常権限で起動し、「更新と修復」の本体版が1.0.0であること、保存先・設定・履歴を確認します。保存済みメディアはその場所に残ります。
4. 旧部品構成が新版本体へ対応していない場合、互換性検証に従って同梱構成へ復旧することがあります。対応する署名済み部品構成は公開済みです。「更新と修復」で部品更新を確認してください。署名情報を書き換えて旧構成を使い続けないでください。

旧AppData版を使っている場合の既存案内は、旧版を手動アンインストールしてからProgram Files版を導入する手順です。独自の自動移行はありません。

## 導入時の表示と制約

- 全ユーザー向けにProgram Files配下へ導入します。導入・削除には管理者権限、通常の起動・保存・部品更新には通常権限を使います。
- この版はWindowsコード署名なしです。SmartScreenや不明な発行元の警告が表示される場合があります。公式配布元とhashを確認し、表示内容を確認して導入を判断してください。部品更新のEd25519署名検証は維持しています。
- WebView2がない場合は導入時にインターネット接続が必要です。接続や組織の実行制限で導入できない場合は、Microsoft公式のEvergreen WebView2 Runtimeを導入してから再実行してください。
- ログイン・Cookie・認証が必要な対象、プレイリスト展開、配信中のライブ録画、他サイトはこの無料版の対象外です。
- サービス側の変更、botアクセス確認、HTTP 403、すべての映像・音声形式への対応は保証しません。保存可能な内容の権利・利用条件は利用者が確認してください。
- 推定残り時間は現在取得しているストリームの目安であり、保存全体の完了時刻ではありません。

問い合わせは[X @legion_edge_dev](https://x.com/legion_edge_dev)が主窓口、[GitHub Issues](https://github.com/legion-edge/simple-media-downloader-releases/issues)が補助窓口です。GitHub投稿にはアカウントが必要です。

利用条件の全文は[APPLICATION-TERMS.txt](APPLICATION-TERMS.txt)、同梱版と対応ソースは[第三者告知](THIRD-PARTY-NOTICES.md)、初回保存と削除は[利用案内](README.md)を参照してください。
