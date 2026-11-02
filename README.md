# Simple Media Downloader

Windows 11 x64向けの、日本語で使えるYouTube・Twitch保存アプリです。このリポジトリでは配布物、利用条件、リリースノート、不具合報告窓口を公開します。アプリ本体のソースコードは公開していません。

## ダウンロード

最新の **v1.1.1** は2026-11-02（JST）公開です。[v1.1.1のダウンロードページ](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v1.1.1)から次の2ファイルを配布します。

| ファイル | サイズ（bytes） | SHA256 |
| --- | ---: | --- |
| [Simple.Media.Downloader_1.1.1_x64-setup.exe](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.1.1/Simple.Media.Downloader_1.1.1_x64-setup.exe) | 107447363 | `89af2749b2f5900f4c51b7f31075c71a764a0dfec7ed29b4459e03f7eff70b96` |
| [distribution-manifest.json](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/v1.1.1/distribution-manifest.json) | 8255 | `3fa97e8cab41aa77d64b68b91f4caf1b92a3c3e80f350c5dea7b61b791d3a8e4` |

manifestにあるinstaller名は`Simple Media Downloader_1.1.1_x64-setup.exe`です。公開assetには空白を含まない名前を使いますが、内容・サイズ・SHA256は同じです。manifestのcommitは非公開本体のビルド元`72ae84d92f3525706789ac86e4b8e6d655057433`です。

`components-`で始まるReleaseはアプリ内の部品更新用です。GitHubが自動表示する「Source code」archiveにinstallerは含まれません。必ず上記のsetup exeを使ってください。

## FreeとPro

v1.1.1はFreeとProで同じアプリを使います。購入ライセンスがなくてもFree機能を利用でき、購入後は「保存設定」の「Pro購入ライセンス」からライセンスキーを確認するとPro機能が有効になります。

- Free: 公開YouTube通常動画・Shorts、公開Twitch VOD・Clipの単体保存、MP4／MP3、履歴・更新確認など。
- Pro: プレイリスト展開、YouTube／Twitchライブ録画、本人が視聴権限と保存許可を確認した認証付き媒体など。

対象サービス側の仕様変更、公開状態、bot確認、HTTPエラー、ネットワークや組織の制限により保存できない場合があります。すべての形式や再生方法への対応は保証しません。詳しくは[Webマニュアル](https://legion-edge.dev/smd/manual/)を確認してください。

## 共用配布: WebP JPEG Converter 1.1.0

このリポジトリでは、WebP JPEG ConverterのWindows x64向けポータブルZIPも配布します。[WebP JPEG Converter 1.1.0のRelease](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/webp-v1.1.0)から次のファイルを取得できます。

| ファイル | サイズ（bytes） | SHA256 |
| --- | ---: | --- |
| [WebpZipConverter-1.1.0-windows-x64.zip](https://github.com/legion-edge/simple-media-downloader-releases/releases/download/webp-v1.1.0/WebpZipConverter-1.1.0-windows-x64.zip) | 21323669 | `1e0fb0128dfa7f2cbf03a6b45f442adbda6e29b30f9ea435c1c03b3a75d9eca9` |

これはSimple Media Downloader本体・installer・部品更新ではありません。`webp-`で始まるタグは、Simple Media Downloaderの本体更新確認では版番号として認識されません。ZIPを別のフォルダーへすべて展開し、`WebpZipConverter.exe`を起動してください。Windowsコード署名はありません。

ダウンロード後はPowerShellでSHA256を確認できます。

```powershell
Get-FileHash -LiteralPath '.\Simple.Media.Downloader_1.1.1_x64-setup.exe' -Algorithm SHA256
Get-FileHash -LiteralPath '.\distribution-manifest.json' -Algorithm SHA256
```

## 動作環境と導入・更新

- Windows 11 x64専用です。setupはProgram Files配下へ全ユーザー向けに導入するため、導入・削除には管理者権限が必要です。通常の起動・保存・部品更新は標準ユーザーで行います。
- Windowsコード署名はありません。SmartScreenが不明な発行元の警告を表示する場合があります。配布元とSHA256を確認し、表示内容を確認して導入を判断してください。
- WebView2 Runtimeがない場合、setupがMicrosoftのbootstrapperを取得するためインターネット接続が必要です。
- Node、Rust、yt-dlp、Deno、FFmpegの別途導入やPATH設定は不要です。

旧版から更新する場合は、アプリを終了して新しいsetupを実行します。設定・履歴・保存済み媒体は保持されます。更新後は「更新と修復」で本体版と部品の状態を確認してください。

## 基本の保存

1. スタートメニューから「Simple Media Downloader」を起動します。
2. 保存先を選び、対象URLを追加します。
3. MP4／MP3と画質・音質を確認して保存を開始します。
4. 完了後は履歴から保存先を開いて確認します。

同じURLは同時に1件だけ処理し、失敗した項目は個別に再試行できます。設定と最新100件の履歴は次回起動後も保持します。

## 更新と修復

本体の更新確認はこのリポジトリの正式な`vX.Y.Z` Releaseだけを対象にします。取得・インストールは手動で、自動更新や無人更新は行いません。

部品更新は別の仕組みです。署名済みmanifestを固定公開鍵で検証し、yt-dlp、Deno、FFmpegなどを更新します。途中で失敗した場合は以前の正常構成または同等構成へ戻します。

## 削除とデータ保持

Windowsの「インストールされているアプリ」から管理者権限を使って削除できます。アプリ本体と同梱部品は削除しますが、利用者が選んだ保存先の媒体は削除しません。

設定、履歴、取得済み更新部品、購入ライセンスの保護データは`%LOCALAPPDATA%\jp.legionedge.simple-media-downloader`に残ります。完全に削除する場合は、必要な媒体を退避し、アプリ終了後に利用者自身でこの専用フォルダーを削除してください。

## 問い合わせ

[問い合わせフォーム](https://docs.google.com/forms/d/e/1FAIpQLSdG1TYaue14khNdVW9KcRstt9DUkRtrgl3aBqkG00UuulYHzQ/viewform)、[X @legion_edge_dev](https://x.com/legion_edge_dev)、または[GitHub Issues](https://github.com/legion-edge/simple-media-downloader-releases/issues)を利用できます。

本体版、Windows版、再現手順、期待した結果と実際の結果を知らせてください。個人情報、認証情報、Cookie、購入ライセンス、限定コンテンツのURL、媒体そのものは公開しないでください。

## 利用条件と第三者ソフトウェア

Free機能は無料で利用できます。Pro機能には正規に発行された購入ライセンスが必要です。無変更の公開バイナリは、[APPLICATION-TERMS.txt](APPLICATION-TERMS.txt)、第三者ライセンス、同梱の`THIRD-PARTY-NOTICES.txt`と`licenses`フォルダーを保持する条件で転載・再配布できます。本体ソースは非公開です。

第三者ソフトウェアには各権利者のライセンスが適用されます。[採用版・対応ソース・通知](THIRD-PARTY-NOTICES.md)を確認してください。

## 過去の公開

- [v1.1.0 Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v1.1.0)
- [v1.0.0 Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v1.0.0)
- [v0.1.0 Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/v0.1.0)

過去のRelease、タグ、asset、利用条件は削除せず保持します。
