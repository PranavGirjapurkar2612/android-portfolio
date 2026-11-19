# Android engineering portfolio
**Pranav Girjapurkar** · Android interfaces, media applications, and APK analysis

I design Android interfaces for tasks that usually start at a command line. REA Pocket UI brings file inspection to a phone, and m314 Flow makes long-running media jobs easier to follow. In CineFlow, the focus is keeping playback, watch history, and saved titles together.

| Project | Android work | Stack |
| --- | --- | --- |
| [REA Pocket UI](PORTFOLIO.md#rea-pocket-ui) | A local workspace for inspecting an APK or archive, viewing bytes and strings, and exporting a report through Android’s file picker. | Java · ARM64 Node.js |
| [m314 Flow](PORTFOLIO.md#m314-flow) | A queue that puts track selection, transfer progress, and job diagnostics in one mobile workflow. | Java · HTML/CSS/JavaScript · FFmpeg |
| [CineFlow](PORTFOLIO.md#cineflow) | A media client that connects search, a watchlist, playback controls, and an offline library. | Java · AndroidX Media3 |

## Design notes from REA Pocket UI

In **REA Pocket UI**, a file moves through three views. **Workspace** holds the imported file. **Tools** lets the user choose an inspection task. **Activity** keeps the result and diagnostics together so the report can be revisited or exported. The mobile interface packages the upstream REA tools and a Termux Node.js runtime. [Implementation notes and credits](PORTFOLIO.md#rea-pocket-ui)

## Build catalog

The catalog covers **15 Android builds**, including independent clients, integrations, and third-party package studies. Each write-up identifies the version, describes the evidence available from the package, and credits upstream tools where applicable. The review covers packaged code and resources. On-device behavior and live service compatibility remain unverified.

[Browse the full catalog](PORTFOLIO.md) · [View published releases](https://github.com/PranavGirjapurkar2612/android-portfolio/releases) · [GitHub profile](https://github.com/PranavGirjapurkar2612)
