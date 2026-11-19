# Android build catalog

Package notes for 15 Android builds reviewed by Pranav Girjapurkar. Versions and runtime details come from static APK inspection. Individual write-ups distinguish observed package contents from owner-reported changes.

[Portfolio overview](README.md) · [Project write-ups](#android-project-write-ups) · [Academic work](#college-work)

## Builds and releases

The catalog lists all 15 supplied builds. The project write-ups contain feature details, tech stacks, and upstream credits.

| App | Version | Features and changes | GitHub entry |
| --- | --- | --- | --- |
| Airtel | 4.154.3 | Kotlin and React Native build with a verified APK archive and signature. | [Download APK](https://github.com/PranavGirjapurkar2612/android-portfolio/releases/download/android-apps-2026-11-17/Airtel-4.154.3.apk) |
| CineFlow | 1.7.0 | Independent MovieBox client with catalog search, playback controls, and an offline library. | [Download APK](https://github.com/PranavGirjapurkar2612/android-portfolio/releases/download/android-apps-2026-11-17/CineFlow-1.7.0.apk) |
| Cinedubs | 1.0.52 | ARM64 build with a verified APK archive and signature. | [Download APK](https://github.com/PranavGirjapurkar2612/android-portfolio/releases/download/android-apps-2026-11-17/Cinedubs-1.0.52.apk) |
| DASH-DL | 1.8.33 | Download queues, presets, diagnostics, and custom scripts. The project notes list integrations for Netflix, ZEE5, Sony LIV, and Hotstar. | [Write-up](#dash-dl) |
| JioHotstar | 26.10.12.2 | ARM64 target build supplied for Android packaging review. | [Write-up](#third-party-package-studies) |
| JioHotstar Modder | 2.6 | Reported changes to ad-related screens and recurring pop-ups. | [Write-up](#packaging-utilities) |
| m314 Flow | 1.1.0 | Playlist and manifest import, track selection, batch jobs, live recording, and segment merging. | [Download APK](https://github.com/PranavGirjapurkar2612/android-portfolio/releases/download/android-apps-2026-11-17/m314-Flow-1.1.0.apk) |
| PatchLens | 2.3.8 | APK inspection, resource optimization, and output verification. Profiles include Comparify, ZEE5, Pocket Films, and Tincat. | [Write-up](#packaging-utilities) |
| Pawxy | 1.15.1 | Requested banner-ad removal and changes to VPN and premium limits. | [Write-up](#third-party-package-studies) |
| Prime Video Clone | 3.0.477.1447 | Separate Android package with reported ad removal and certificate-pinning changes. | [Write-up](#third-party-package-studies) |
| REA Pocket UI | 1.0.1 | Local APK, archive, and binary analysis with REA tools, hex and string views, and report export. | [Download APK](https://github.com/PranavGirjapurkar2612/android-portfolio/releases/download/rea-pocket-ui-v1.0.1/REA-Pocket-UI-1.0.1.apk) |
| Sony LIV | 6.38.20 | Reported preview-access changes, ad removal, and certificate-pinning changes. | [Write-up](#third-party-package-studies) |
| Tincat Pro | 5.3.1-iptv4.6 | Reported premium entitlement changes and support for IPTV and encrypted MPEG-DASH (MPD/CENC) playlists. | [Write-up](#third-party-package-studies) |
| Vine Studio | 1.0.1 | Provider and episode discovery, track selection, queued jobs, and a local media library. | [Write-up](#vine-studio) |
| ZEE5 | 39.63.3 | Reported ad removal and certificate-pinning changes. | [Write-up](#third-party-package-studies) |

## Review method

I use AI-assisted prototyping to explore interface ideas and investigate errors. For each build, I distinguish the Android host from bundled runtimes, record the package version, and identify upstream components. A library or profile shipped in an APK establishes its presence in the package. Runtime compatibility requires a separate on-device test.

## Android project write-ups

### REA Pocket UI

<details>
<summary>REA Pocket UI 1.0.1 · Android file analysis</summary>

An independent Android adaptation of **REA (Reverse Engineer Anything)**. **Workspace** holds imported files, **Tools** provides access to the packaged catalog, and **Activity** keeps results and diagnostic reports together.

- Import APKs, archives, binaries, source files, and folders into a local workspace.
- Inspect APK and ZIP contents, native architectures, DEX files, and archive metadata. View file bytes in hex or search printable strings with their offsets.
- Browse and star tools. The packaged catalog contains **255 entries** and the build ships an ARM64 Node.js runtime.
- Start local jobs, revisit results and diagnostic reports, and export a report through Android's file picker.

**Stack.** Java Android host and bundled ARM64 Node.js with JavaScript and TypeScript tooling.

**Upstream REA.** The original project provides a CLI and an MCP interface for connecting its tools to AI assistants. It covers APK resources and signatures, native binaries through decompiler integrations, JavaScript and Electron bundles and source maps, .NET assemblies, and firmware. It also includes workflows for SQLite databases, WebAssembly, websites, and saved captures. Some workflows require desktop tooling or additional host dependencies.

**Credits.** Original REA by **morluto and contributors** under the MIT license. The mobile package identifies upstream REA **6.9.0** and credits Termux for its Node.js runtime. [Original REA repository](https://github.com/morluto/rea) · [Upstream revision bundled in REA Pocket](https://github.com/morluto/rea/tree/d6bcfc10eafa3c0893c7cbd5f3dc6a90359be022)

</details>

### Vine Studio

<details>
<summary>Vine Studio 1.0.1 · Mobile media workspace</summary>

A VT-inspired Android interface that takes a media job from discovery to a searchable local library. It combines a Java Android host, a web interface, and a bundled Python runtime with distinct engine and discovery components.

- **Discover.** Browse categories where supported, search for titles by provider, or enter program and manifest links. The shipped catalog lists 10 browsing entries and 74 download-service entries.
- **Plan a job.** Inspect available tracks, select episodes, set quality and language preferences, and stage multiple links as a batch.
- **Run and monitor.** Choose an engine, follow the queue and progress, review recent activity, and respond to selection prompts when a job needs input.
- **Manage files.** Search saved output from the Files view and open the finished files from the same workspace.
- **Configure the workspace.** Review engine readiness, manage service profiles, configure advanced workflows and content-protection settings, choose the appearance, and read built-in help and license notices.

**Credits.** The build credits the Unshackle, Envied, and VineFeeder contributors and the m314 Flow base interface. VT is the stated inspiration. The exact VT repository and revision are still to be confirmed. Catalog entries and settings indicate what the build exposes. Service availability depends on the source and account access.

</details>

### m314 Flow

<details>
<summary>m314 Flow 1.1.0 · Android interface for stream tools</summary>

Wraps established command-line media engines in an Android interface for choosing sources, controlling transfers, and managing the resulting files.

- Import links, media manifests, and IPTV playlists. Inspect tracks and choose entries for batch jobs.
- Set video quality, subtitle output, video codec, and output container. Use local manifests or segment folders for merging workflows.
- Start live recordings, follow progress, resume transfers, and review job diagnostics and saved files.
- Configure broadcast output and server modes when working with streams authorized for redistribution.

**Stack.** Java Android host and an HTML/CSS/JavaScript interface. The native tools include m314dl (Go), VSD (Rust), and FFmpeg.

**Credits.** The archive bundles **m314dl**, **VSD**, and **FFmpeg**. [m314dl by m314](https://m314.dev/) · [VSD by clitic and contributors](https://github.com/clitic/vsd) · [FFmpeg project](https://ffmpeg.org/)

</details>

### CineFlow

<details>
<summary>CineFlow 1.7.0 · Independent MovieBox client</summary>

A native Android client that combines film and series discovery, playback, and offline viewing in one interface. MovieBox is the upstream service. CineFlow is an independent client.

- **Discovery.** Featured and trending films and series, title search with recent searches, and sorting and filters for genre, language, country, and age rating. A catalog cache supports browsing previously loaded results.
- **Title details.** Trailers, shareable title details, and season and episode navigation. Add items to **My List**, mark titles watched or unwatched, and return through **Continue Watching** or history.
- **Playback.** Quality selection, alternate audio versions, audio and subtitle tracks, next-episode controls, playback speed, picture-in-picture, a sleep timer, and a control lock. A separate screen accepts video links.
- **Offline library.** Queue a film or episode, follow progress, pause or resume transfers, and play or remove saved files. Download quality and network preferences include a Wi-Fi-only option.
- **Account and appearance.** Optional use of an existing MovieBox account through its approval flow. The APK includes a TV activity, selectable themes, and controls for collecting or copying crash and connection reports.

The stack is **Java and AndroidX Media3**. This feature list follows the app's screens and packaged code. Playback and catalog access depend on the service.

</details>

### DASH-DL

<details>
<summary>DASH-DL 1.8.33 · Configurable media transfers</summary>

An Android workspace inspired by **N_m3u8DL-RE**. The project brings a command-line stream engine into a graphical workflow with clipboard link intake, queue and activity views, reusable options, completed files, and task diagnostics. The archive also contains provider-specific modules and an embedded Python environment. Custom scripts and content decryption module (CDM) configuration are reported by the project owner. Downloads from individual services were not tested.

The APK contains a **Java** host, **HTML/CSS/JavaScript** for the interface, and packaged media tools. [N_m3u8DL-RE by nilaoda and contributors](https://github.com/nilaoda/N_m3u8DL-RE)

</details>

### Packaging utilities

<details>
<summary>PatchLens, JioHotstar Modder, and Comparify</summary>

**PatchLens 2.3.8** is a Java utility that organizes APK inspection and packaging around per-app profiles. Its interface supports APK selection, resource optimization, and output verification. The package identifies profiles for Comparify, Pocket Films, ZEE5, and Tincat. Profile presence by itself does not establish compatibility with each target build.

**JioHotstar Modder 2.6** is a standalone Android patch-management prototype focused on interruptions in the viewing interface. The reported changes target ad-related surfaces and recurrent pop-ups. Its bundled project contains Java application code and Python build tools. The tool and the JioHotstar target build are separate artifacts.

**Comparify** is a product comparison project for reviewing shopping choices side by side. The supplied files identify Comparify as a PatchLens profile. A standalone Comparify build or source is needed to confirm its language and feature list.

</details>

### Third-party package studies

<details>
<summary>Third-party APK case studies and package notes</summary>

These entries describe packaging experiments and reported client changes. The language column describes the inspected build, including bundled components, and does not assign authorship of the original app.

| Build | Project note | Language or runtime evidence |
| --- | --- | --- |
| **ZEE5 39.63.3** | A playback-interface study focused on ad interruptions and the behavior of the client's certificate pinning. The reported modification adjusts those two areas. | Kotlin app classes and Android JVM bytecode. |
| **Sony LIV 6.38.20** | A viewing-flow experiment covering preview availability, ad interruptions, and client transport checks. Preview, ad, and pinning changes were reported for this variant. | Kotlin metadata in Sony LIV classes, plus native libraries. |
| **Prime Video Clone 3.0.477.1447** | A packaging experiment with a separate Android package ID. Reported work addresses ad surfaces and certificate pinning in the cloned build. | React Native and a Hermes JavaScript bundle. Original JavaScript versus TypeScript source is unconfirmed. |
| **Tincat Pro 5.3.1-iptv4.6** | Extends the browser workflow with IPTV and MPEG-DASH playlist handling. The reported scope includes encrypted stream handling and an entitlement change. | Android JVM bytecode, an embedded Python runtime, and FFmpeg components. Source language for the obfuscated host is unconfirmed. |
| **JioHotstar 26.10.12.2** | Inspected the target APK independently of the Modder tool. The package contains multi-DEX Android code and ARM64 libraries. | Kotlin metadata in app classes and the launcher. |
| **Airtel 4.154.3** | Inspected the app package and identified its native Android and web-runtime layers. | Kotlin, React Native, and a Hermes JavaScript bundle. |
| **Cinedubs 1.0.52** | Recorded the package, version, and ARM64 components for the submitted build. | Android JVM bytecode and native libraries. App source language is unconfirmed. |
| **Pawxy 1.15.1** | Recorded the browser build, its launcher, and its native ARM64 payload. The requested changes included banner-ad removal and changes to VPN and premium limits. | Android JVM bytecode and native libraries. App source language is unconfirmed. |

</details>

## College work

**Study on Supply Chain Management of Nestlé** — Academic research on the company's supply chain processes and operating practices.

<sub>Project versions, packaged features, and tech stacks come from a static review of 15 builds. On-device behavior and service compatibility are unverified.</sub>
