# Simple Media Downloader

Windows 11 x64向けの、日本語で使える無料のYouTube動画・音声保存アプリです。このリポジトリでは配布物、利用案内、不具合報告を扱います。アプリ本体のソースコードは公開していません。

## ダウンロード

無料版完成版 **v1.0.0** を2026-09-20（JST）に公開しました。[公式ダウンロードページ](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v1.0.0)で次の2ファイルを配布しています。

| ファイル | サイズ（bytes） | SHA256 |
| --- | ---: | --- |
| [Simple.Media.Downloader_1.0.0_x64-setup.exe](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.0.0/Simple.Media.Downloader_1.0.0_x64-setup.exe) | 106118436 | `8eff5fa58af274e0d543ef6556749edddd1c10c29e3beffb9e1f106526d836b2` |
| [distribution-manifest.json](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.0.0/distribution-manifest.json) | 7739 | `084787ef97c5c1917185d2f3eaef7d6d15ff43a7274c9a69c3274847ab0448d4` |

manifestにあるビルド時の名前は`Simple Media Downloader_1.0.0_x64-setup.exe`です。公開asset名は空白をピリオドにした名前を使います。内容・サイズ・SHA256は同じです。manifestの`candidate-only`と作成日時はビルド時の記録として保持し、一般公開の実績はこの案内とReleaseに記載します。manifestのcommitは非公開本体のビルド元であり、公開repoのtag対象commitとは別です。

`components-`で始まるReleaseはアプリ内の部品更新用です。GitHubが自動表示する「Source code」archiveにもinstallerは含まれません。導入には上表のsetup exeを使ってください。

ダウンロード先でPowerShellを開き、SHA256を確認できます。

```powershell
Get-FileHash -LiteralPath '.\Simple.Media.Downloader_1.0.0_x64-setup.exe' -Algorithm SHA256
Get-FileHash -LiteralPath '.\distribution-manifest.json' -Algorithm SHA256
```

## v0.1.0からの改善

初回保存先案内、コンパクトな一覧と進捗表示、1列／2列の切替、初期OFFのクリップボードURL取込み、ファイル名書式、チャンネル別フォルダー保存、本体の手動更新確認、問い合わせと診断プレビューを追加・改善しました。詳しくは[v1.0.0リリースノート](RELEASE_NOTES_1.0.0.md)をご覧ください。

## 動作環境と導入・更新

- Windows 11 x64向けです。setupを実行するとProgram Files配下へ全ユーザー向けに導入します。導入・削除には管理者権限が必要です。通常の起動・保存・部品更新は標準ユーザーで行えます。
- Windowsコード署名はありません。SmartScreenや不明な発行元の警告が表示される場合があります。公式配布元とSHA256を確認し、表示内容を確認して導入を判断してください。警告の有無は環境・取得経路により異なります。
- WebView2 Runtimeがない場合は、setupによるMicrosoftのbootstrapper取得にインターネット接続が必要です。導入に失敗した場合は接続と組織の実行制限を確認し、Microsoft公式のEvergreen WebView2 Runtimeを導入してから再実行してください。
- Node、Rust、yt-dlp、Deno、FFmpegの別途導入やPATH設定は不要です。

現行Program Files版v0.1.0からは、アプリを終了して新setupを実行します。**公開済みv0.1.0には本体更新確認ボタンがないため、公式配布ページから手動取得してください。** 設定・履歴・保存済みメディアを保持します。非互換の旧部品構成は同梱構成へ復旧する場合があります。更新後に「更新と修復」で本体版1.0.0と部品の状態を確認してください。

旧AppData版を利用している場合は、アプリを終了して旧版を手動アンインストールしてからProgram Files版を導入してください。設定・履歴・更新構成の専用フォルダーと保存済みメディアは削除しないでください。独自の自動移行はありません。

## 初回の保存

1. スタートメニューから「Simple Media Downloader」を起動します。
2. 保存先を選び、YouTubeの通常動画またはShortsのURLを1行に1件ずつ追加します。
3. MP4／MP3と、画質／音質／音声を確認して保存を開始します。初期値はMP4 Full HD、MP3 192kbpsです。
4. 完了後は「保存場所を開く」からファイルを確認します。

複数URLは同時1件ずつ処理し、件別に停止・同じ条件で再試行できます。設定と最新100件の履歴は次回起動後も保持します。

## 更新と修復

v1.0.0では利用者が本体の更新確認を選んだときだけ、公式Releaseの新版を確認します。取得・インストールは手動で、自動確認・自動更新は行いません。

部品更新は別の機能です。この公開repoの`components-stable`をHTTPSで取得し、本体に固定したEd25519公開鍵で署名を検証して、yt-dlp、Deno、FFmpeg等の構成を適用します。問題時は以前の正常構成または同梱構成へ戻せます。部品の署名検証はWindowsコード署名とは別の仕組みです。

## 削除とデータ保持

Windowsの「インストールされているアプリ」から管理者権限を許可して削除できます。アプリ本体と同梱部品は削除しますが、利用者が選んだ保存先のメディアは削除しません。

設定、履歴、取得した更新構成は、再導入や調査のため`%LOCALAPPDATA%\jp.legionedge.simple-media-downloader`に残します。完全に削除する場合は、アプリを終了し、必要なメディアを退避してから、この専用フォルダーを利用者自身で削除してください。

## 対応範囲と制約

- ログイン不要で取得できるYouTube通常動画・ShortsをMP4／MP3へ保存します。プレイリスト展開、ログイン・Cookie・認証が必要な対象、配信中のライブ録画、他サイトは対象外です。
- サービス側の変更、botアクセス確認、HTTP 403、ネットワーク・組織の制限により保存できない場合があります。すべての形式や再生機器への対応は保証しません。
- 推定残り時間は現在取得中のストリームの目安です。結合・変換を含む保存全体の完了時刻ではありません。
- 保存する内容の権利と各サービスの利用条件を確認し、必要な許可を得てください。

## 問い合わせ

[X @legion_edge_dev](https://x.com/legion_edge_dev)を主窓口、[GitHub Issues](https://github.com/legion-edge/simple-media-downloader-releases/issues)を詳しい不具合報告の補助窓口としています。GitHubへの投稿にはアカウントが必要です。

本体版、Windowsの版、再現手順、期待と実際の結果をお知らせください。v1.0.0の「問い合わせ」には共有前に内容を確認できる診断プレビューと手動コピーがあります。自動送信はしません。個人情報、認証情報、Cookie、生ログ、署名付きメディアURL、メディア自体は公開しないでください。

## 利用条件と第三者ソフトウェア

v1.0.0は無料で利用できます。変更していない公式配布バイナリは、利用条件と第三者告知を保持すれば転載・再配布できます。[APPLICATION-TERMS.txt](APPLICATION-TERMS.txt)、`THIRD-PARTY-NOTICES.txt`と`licenses`フォルダーを保持してください。本体ソースは非公開で、OSSライセンスを付与していません。

第三者ソフトウェアには各権利者のライセンスが適用されます。[採用版・対応ソース・同梱告知](THIRD-PARTY-NOTICES.md)を確認してください。

## 過去の公開

v0.1.0の無料利用・未変更バイナリの転載／再配布許諾は変更しません。当時の条件は[旧利用条件](https://github.com/legion-edge/simple-media-downloader-releases/blob/721d3d780fc284fa6ebd438948d25d2e895ba3ee/APPLICATION-TERMS.txt)で確認できます。2026-09-14の初回公開と、告知前の同版Program Files版への差し替えは[v0.1.0リリースノート](RELEASE_NOTES_0.1.0.md)に保持しています。[旧Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v0.1.0)のtagと2assetは維持しています。
