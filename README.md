# Simple Media Downloader

Windows 11 x64向けの、日本語で使える動画・音声ダウンローダーです。

このリポジトリは、配布ファイル、リリースノート、利用案内、不具合報告・要望の窓口として使用します。アプリ本体のソースコードは公開していません。

## 2026-09-14の配布物更新

告知前の修正として、同じv0.1.0のinstallerとmanifestを更新しました。現在の配布物はProgram Files配下への全ユーザー向け導入に対応し、起動時の内部確認だけが動いている場合の不要な終了確認を改善しています。

以前のAppData版を導入済みの場合は、アプリを終了して旧版を手動アンインストールしてから、新しいsetupを実行してください。設定・履歴・更新構成のフォルダーと保存済みメディアは削除しないでください。自動移行機能はありません。

配布物の識別には下表のSHA256を使用してください。v0.1.0タグは初回公開時の案内を指したまま維持し、現在の案内はmainに掲載しています。manifestのcommitは非公開のアプリ本体のビルド元を示し、公開案内のcommitとは別です。

## 配布状況

**初版v0.1.0を公開しました。** [v0.1.0のダウンロードページ](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v0.1.0)からWindows用installerを取得できます。

[Releases](https://github.com/legion-edge/simple-media-downloader-releases/releases)にある`components-`で始まるReleaseは、アプリ内の「更新と修復」で使う部品用です。Windows installer本体ではありません。

[v0.1.0 Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v0.1.0)で次の2ファイルを配布しています。

| 配布ファイル | サイズ | SHA256 | 現在の状態 |
| --- | ---: | --- | --- |
| `Simple.Media.Downloader_0.1.0_x64-setup.exe` | 106,062,709 bytes | `c1e440593940621e1f97d46be01cefb53bc15666b79f529a5210fddd6da08503` | 公開済み |
| `distribution-manifest.json` | 7,294 bytes | `673cd89404851030982abc2edd5a1fe6e4259459d40daa8a47daa953c05eef4f` | 公開済み |

GitHubのasset名の処理により、installer名の空白はピリオドになっています。manifestに記録したビルド時の名前は`Simple Media Downloader_0.1.0_x64-setup.exe`ですが、ファイル内容・サイズ・SHA256は同一です。manifestは元のビルド記録を変更せず配布しています。

ダウンロードしたファイルのSHA256を次のように確認できます。

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Simple.Media.Downloader_0.1.0_x64-setup.exe'
Get-FileHash -Algorithm SHA256 -LiteralPath '.\distribution-manifest.json'
```

## 動作環境と導入

- 対象はWindows 11 x64です。他のOSとCPUは初版の対象外です。
- `Simple.Media.Downloader_0.1.0_x64-setup.exe`を実行すると、Program Files配下へ全ユーザー向けに導入します。導入・削除には管理者権限が必要です。通常の起動・保存・部品更新は標準ユーザーで行えます。
- Windowsコード署名は行っていないため、発行元やアプリの信頼性に関する警告が表示される場合があります。配布元がこのリポジトリであることと、上記SHA256が一致することを確認してください。
- WebView2 Runtimeがない環境では、setupがMicrosoftのbootstrapperを取得するため、その時だけインターネット接続が必要です。取得や導入に失敗した場合は、接続と組織の実行制限を確認し、Microsoft公式のEvergreen WebView2 Runtimeを導入してからsetupを再実行してください。

利用者がNode、Rust、yt-dlp、Deno、FFmpegを別途導入したり、PATHを設定したりする必要はありません。セキュリティ機能を一律に無効化しないでください。

## 初回の保存

1. スタートメニューから「Simple Media Downloader」を起動します。
2. 保存先を選び、YouTubeの通常動画またはShortsのURLを1行に1件ずつ追加します。
3. MP4／MP3と、画質／音質／音声を確認して保存を開始します。初期値はMP4 Full HD、MP3 192kbpsです。
4. 完了後は「保存場所を開く」からファイルを確認します。

複数URLは同時1件ずつ処理し、件別に停止・同じ条件で再試行できます。設定と最新100件の履歴は次回起動後も保持します。

## 更新と修復

「更新と修復」は、同梱したyt-dlp、Deno、FFmpeg等の部品構成を確認・更新・復旧する機能です。アプリ本体の自動更新ではありません。

更新情報は、この公開リポジトリの`components-stable` ReleaseからHTTPSで取得し、アプリ本体に固定したEd25519公開鍵で署名を検証します。問題がある場合は、以前の正常構成または同梱構成へ戻せます。Windowsコード署名とは別の仕組みです。

## 削除とデータ保持

Windowsの「インストールされているアプリ」から管理者権限を許可して削除できます。アプリ本体と同梱部品は削除しますが、利用者が選んだ保存先のメディアは削除しません。

設定、履歴、取得した更新構成は、再導入や調査のため`%LOCALAPPDATA%\jp.legionedge.simple-media-downloader`に残します。完全に削除する場合は、アプリを終了し、必要なメディアを退避してから、この専用フォルダーを利用者自身で削除してください。

## 既知の制限

- 対象はYouTubeの公開された通常動画とShortsです。プレイリスト全件、ログインが必要な動画、非公開動画、ライブ配信、他サイトには対応しません。
- 配信元の仕様変更、アクセス制限、ネットワークや組織のポリシーにより、情報取得や保存が失敗する場合があります。
- 初版はWindowsコード署名なしのため、SmartScreen等の表示は環境や取得経路によって異なります。警告が表示されないことは保証しません。
- 保存するコンテンツについて、著作権その他の権利と各サービスの利用条件を確認し、必要な許可を得てください。

## 不具合報告・要望

[GitHub Issues](https://github.com/legion-edge/simple-media-downloader-releases/issues)を主な窓口として受け付けます。日本語で投稿できます。

アプリのバージョン、Windowsのバージョン、再現手順、期待した結果と実際の結果を記載してください。個人情報、認証情報、署名付きメディアURLを含むログは掲載しないでください。Xのアカウントは未確定であり、問い合わせに必要ありません。

## 利用条件と第三者ソフトウェア

v0.1.0は無料でダウンロード、インストール、利用できます。変更していない公式配布バイナリは、利用条件と第三者告知を保持したまま転載・再配布できます。詳しくは[使用・再配布条件](APPLICATION-TERMS.txt)を確認してください。

yt-dlp、EJS、Deno、FFmpeg等には各権利者のライセンスが適用されます。採用版、対応ソース、同梱する告知は[第三者ソフトウェアの案内](THIRD-PARTY-NOTICES.md)にまとめています。installerにはライセンス本文と固定した第三者告知を同梱します。

v0.1.0の変更点と注意事項は[リリースノート](RELEASE_NOTES_0.1.0.md)で確認できます。
