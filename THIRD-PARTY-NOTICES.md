Simple Media Downloader 1.1.0 - third-party notices index
================================================================

This file describes the fixed third-party software in the Windows x64
distribution candidate. Application use and binary redistribution terms are
separate; see APPLICATION-TERMS.txt.

Bundled executables
-------------------

yt-dlp 2026.08.19 (official Windows PyInstaller executable)
  Executable SHA256: 66674953fe251b89f4d08c5f0e35e0728679bd67ab3d7d05c0562af101dd3e7a
  Upstream: https://github.com/yt-dlp/yt-dlp/releases/tag/2026.08.19
  Corresponding source: https://github.com/yt-dlp/yt-dlp/tree/2026.08.19
  License: GPL-3.0-or-later for the combined PyInstaller executable. yt-dlp
  itself uses the Unlicense. See licenses/yt-dlp-LICENSE.txt and
  licenses/yt-dlp-THIRD-PARTY-LICENSES.txt.

yt-dlp-ejs 0.8.0 (embedded in the official yt-dlp executable)
  Upstream and source: https://github.com/yt-dlp/ejs/tree/0.8.0
  License: Unlicense; the built EJS package also contains ISC-licensed
  meriyah and MIT-licensed astring. Their texts are included in the yt-dlp
  third-party file. See licenses/ejs-LICENSE.txt.

Deno 2.9.6 (official x86_64-pc-windows-msvc executable)
  Executable SHA256: 2ff9493dfa356be2975f477025ea770088e9e9cb2c83d983236d13561b96b7a6
  Upstream: https://github.com/denoland/deno/releases/tag/v2.9.6
  Corresponding source: https://github.com/denoland/deno/tree/v2.9.6
  License: MIT. See licenses/deno-LICENSE.txt and
  licenses/DENO-SOURCE-LICENSES.txt. The official binary archive does not
  provide an aggregate third-party dependency notice (upstream issue #13515),
  so this distribution supplies its own fixed-source inventory:

  - licenses/DENO-CARGO-DEPENDENCIES-LICENSES.txt covers all 887 Windows
    normal and build packages selected from the v2.9.6 Cargo.lock with
    cargo-about 0.9.2. Every package is linked to collected license text.
    Generic MIT/BSD templates with copyright placeholders were detected for
    93 packages. Packaged notices, the exact Deno/rusty_v8 trees, or notices
    from fixed upstream commits replace them for 84 packages. Source copyright
    and license headers with fixed paths and hashes supplement 2 more packages.
    For the remaining 7 fixed sources that contain neither a root notice nor a
    matching source header, the package metadata, repository, VCS commit,
    manifest hash, and declared SPDX text are recorded explicitly rather than
    treating the template as package-specific text.
  - licenses/DENO-V8-SOURCE-LICENSES.txt covers rusty_v8 150.4.0, V8
    15.0.245.2, ICU 77.1, and every license-like file or README.chromium in the
    exact rusty_v8 source tree and its 20 pinned submodules. Its 728-file
    inventory is intentionally a conservative superset, including build- and
    test-only source that might not be linked into deno.exe.
  - licenses/typescript-LICENSE.txt covers the bundled TypeScript 6.0.3
    compiler. licenses/rust-stdlib-LICENSE-APACHE.txt,
    licenses/rust-stdlib-LICENSE-MIT.txt, and
    licenses/rust-stdlib-COPYRIGHT.txt cover the Rust 1.95.0 standard library.

  Reproduction inputs and exact source commits are recorded in
  docs/DISTRIBUTION.md in the development repository. The upstream gap remains
  documented at https://github.com/denoland/deno/issues/13515; this distribution
  does not depend on the incomplete upstream archive for its notice set.

FFmpeg and ffprobe 9.0.1-essentials_build-www.gyan.dev
  ffmpeg SHA256: 72a489eccd008c2ec2c0a5856c5c75bc3d8bbfa90166c4566865c246445e6aa3
  ffprobe SHA256: 19202b23c0043f15ad1b7bce2344f406fd52bd6efd8f995ce02e7392a1cec52f
  Binary build: https://github.com/GyanD/codexffmpeg/releases/tag/9.0.1
  Build scripts: https://github.com/GyanD/codexffmpeg/tree/9.0.1
  Corresponding FFmpeg source: https://github.com/FFmpeg/FFmpeg/commit/bf1b838f2a
  License: GPL-3.0-or-later for this configured static build. See
  licenses/ffmpeg-LICENSE.txt and licenses/ffmpeg-README.txt for the license,
  configuration, enabled libraries, and upstream source locations shipped by
  the binary distributor.

Application dependencies
------------------------

The release application also includes compiled Rust crates and bundled
JavaScript packages fixed by Cargo.lock and package-lock.json. Their exact
package names, versions, declared license expressions, source repositories,
and license/notice texts are generated during candidate preparation in
licenses/APP-DEPENDENCIES-LICENSES.txt. Candidate creation fails when this
file or any fixed component notice is absent, empty, or does not match its
pinned input.

The application's Rust standard library is separate from Deno's fixed Rust
1.95.0 inventory above. licenses/APP-RUST-STDLIB-VERSION.txt identifies the
compiler actually used for this candidate, and
licenses/APP-RUST-STDLIB-COPYRIGHT.html preserves that installed toolchain's
complete standard-library copyright and license inventory.

WebView2 and installer tooling
------------------------------

Microsoft Edge WebView2 Runtime is not copied into this candidate. Windows 11
normally provides it. If it is absent, the NSIS installer downloads and runs
Microsoft's WebView2 bootstrapper; internet access is required at that stage.
The NSIS installer and Tauri bundler are build tools, not application features.

Source and changes
------------------

No modifications are made to the four bundled executables. Exact upstream
archives, hashes, build configuration, source locations, and notice generation
inputs are recorded in docs/DISTRIBUTION.md in the private development
repository. Public binaries, hashes, use terms, notices, and support are hosted
at https://github.com/legion-edge/simple-media-downloader-releases. The release
notes and final distribution manifest identify the exact application commit
used to build a candidate.
