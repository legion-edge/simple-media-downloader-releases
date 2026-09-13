# 第三者ソフトウェアの案内

Simple Media Downloader v0.1.0のWindows x64配布物には、次の固定した第三者ソフトウェアを変更せずに同梱します。各ソフトウェアには、それぞれの権利者が定めたライセンスが適用されます。

| 部品 | 採用版 | ライセンス・対応ソース |
| --- | --- | --- |
| yt-dlp | 2026.08.19 | 公式Windows PyInstaller実行ファイルはGPL-3.0-or-later。[対応ソース](https://github.com/yt-dlp/yt-dlp/tree/2026.08.19) |
| yt-dlp EJS | 0.8.0 | Unlicense。ビルド内のmeriyahはISC、astringはMIT。[対応ソース](https://github.com/yt-dlp/ejs/tree/0.8.0) |
| Deno | 2.9.6 | MIT。[対応ソース](https://github.com/denoland/deno/tree/v2.9.6) |
| rusty_v8／V8 | rusty_v8 150.4.0／V8 15.0.245.2 | [rusty_v8対応commit](https://github.com/denoland/rusty_v8/tree/5c15a6995c9bb4bacd3e341b59fff32c909c80bf)／[V8対応commit](https://chromium.googlesource.com/v8/v8/+/ac1e23989121713ca642f6650b34deff7b686896) |
| TypeScript | 6.0.3 | Apache-2.0。[対応ソース](https://github.com/microsoft/TypeScript/tree/v6.0.3) |
| Rust標準ライブラリ | 1.95.0 | Apache-2.0 OR MIT。[対応ソース](https://github.com/rust-lang/rust/tree/1.95.0) |
| FFmpeg／ffprobe | 9.0.1 essentials build | 採用構成はGPL-3.0-or-later。[ビルド手順](https://github.com/GyanD/codexffmpeg/tree/9.0.1)／[FFmpeg対応commit](https://github.com/FFmpeg/FFmpeg/commit/bf1b838f2a) |

installerには`THIRD-PARTY-NOTICES.txt`と`licenses`フォルダーを収録します。そこには、上記部品のライセンス本文、yt-dlpの第三者告知、DenoのWindows通常・build依存、Deno source内の個別本文、rusty_v8／V8の固定source告知、TypeScript、Rust標準ライブラリ、FFmpegのライセンス・build構成・対応ソース、および製品のRust／JavaScript依存の告知を含めます。

公開する`distribution-manifest.json`には、同梱した告知ファイルの名前、サイズ、SHA256を記録します。再配布する場合は、`APPLICATION-TERMS.txt`、`THIRD-PARTY-NOTICES.txt`、`licenses`フォルダーを削除せず、各ライセンスの条件に従ってください。

[部品構成Release](https://github.com/legion-edge/simple-media-downloader-releases/releases/tag/components-win-x64-20260914-1)はアプリの「更新と修復」用です。installer本体ではありませんが、同じ固定部品と告知を含みます。

WebView2 Runtimeはアプリへ同梱しません。Windowsに存在しない場合だけ、installerがMicrosoftのbootstrapperを取得します。
