# Simple Media Downloader v0.1.0 リリースノート

Simple Media Downloaderの初版です。Windows 11 x64で、YouTubeの通常動画とShortsを日本語画面からMP4またはMP3として保存できます。

## 2026-09-14の配布物更新

告知前の修正として、同じv0.1.0のinstallerとmanifestを更新しました。現在の配布物はProgram Files配下への全ユーザー向け導入に対応し、起動時の内部確認だけが動いている場合の不要な終了確認を改善しています。

以前のAppData版を導入済みの場合は、アプリを終了して旧版を手動アンインストールしてから、新しいsetupを実行してください。設定・履歴・更新構成のフォルダーと保存済みメディアは削除しないでください。自動移行機能はありません。

配布物の識別には下表のSHA256を使用してください。v0.1.0タグは初回公開時の案内を指したまま維持し、現在の案内はmainに掲載しています。manifestのcommitは非公開のアプリ本体のビルド元を示し、公開案内のcommitとは別です。

## 配布ファイル

| ファイル | サイズ | SHA256 |
| --- | ---: | --- |
| `Simple.Media.Downloader_0.1.0_x64-setup.exe` | 106,062,709 bytes | `c1e440593940621e1f97d46be01cefb53bc15666b79f529a5210fddd6da08503` |
| `distribution-manifest.json` | 7,294 bytes | `673cd89404851030982abc2edd5a1fe6e4259459d40daa8a47daa953c05eef4f` |

GitHubのasset名の処理により、installer名の空白はピリオドになっています。manifestに記録したビルド時の名前は`Simple Media Downloader_0.1.0_x64-setup.exe`ですが、ファイル内容・サイズ・SHA256は同一です。manifestは元のビルド記録を変更せず配布しています。

## 主な機能

- MP4は4K／1440p／Full HD／720p／480p候補、MP3は320／192／128kbpsから選択
- 複数URLを同時1件ずつ処理し、件別の停止・同じ条件での再試行に対応
- 複数音声の言語、元音声／吹替情報を表示して選択
- MP3へ取得可能な曲名、アーティスト、アルバム、カバー画像を埋め込み
- 設定と最新100件の履歴を保持
- 署名付きstable情報による部品更新と、以前の正常構成／同梱構成への復旧

## 導入と初回保存

1. setup exeと、このページに掲載したSHA256が一致することを確認します。
2. setup exeを実行します。Program Files配下へ全ユーザー向けに導入するため、管理者権限が必要です。通常の起動・保存・部品更新は標準ユーザーで行えます。
3. WebView2 Runtimeがない場合だけ、Microsoftのbootstrapper取得にインターネット接続が必要です。
4. スタートメニューから起動し、保存先、MP4／MP3、画質／音質／音声を確認して保存を開始します。

Node、Rust、yt-dlp、Deno、FFmpegの別途導入や手動PATH設定は不要です。

## 署名と安全確認

初版installerはWindowsコード署名を行っていません。SmartScreenや発行元の警告が表示される場合があり、表示は環境や取得経路で異なります。配布元がこのリポジトリであることと、ファイルのSHA256を確認してください。警告が表示されないことは保証しません。

部品更新にはEd25519署名を使用します。これはWindowsコード署名やアプリ本体の自動更新とは別の仕組みです。

## 更新・修復・削除

「更新と修復」から固定した公開配信の部品更新を確認・適用し、問題時は以前の正常構成または同梱構成へ戻せます。

Windowsの「インストールされているアプリ」から管理者権限を許可して削除できます。保存済みメディアは削除しません。設定、履歴、更新構成は再導入や調査のため`%LOCALAPPDATA%\jp.legionedge.simple-media-downloader`に残します。

## 既知の制限

- Windows 11 x64のみを対象とします。
- プレイリスト全件、ログインが必要な動画、非公開動画、ライブ配信、他サイトには対応しません。
- 配信元の仕様変更、アクセス制限、ネットワークや組織のポリシーにより保存できない場合があります。
- 保存するコンテンツの権利とサービスの利用条件は利用者が確認してください。

## 利用条件・第三者告知・問い合わせ

v0.1.0は無料で利用できます。変更していない公式配布バイナリは、利用条件と第三者告知を保持したまま転載・再配布できます。詳しくは[使用・再配布条件](https://github.com/legion-edge/simple-media-downloader-releases/blob/main/APPLICATION-TERMS.txt)と[第三者ソフトウェアの案内](https://github.com/legion-edge/simple-media-downloader-releases/blob/main/THIRD-PARTY-NOTICES.md)を確認してください。

不具合・要望は[GitHub Issues](https://github.com/legion-edge/simple-media-downloader-releases/issues)へ日本語で投稿できます。Xのアカウントは未確定であり、問い合わせに必要ありません。
