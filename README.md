<div align="center">

<img src="assets/banner.svg" width="100%" alt="Bandwidth Monitor banner"/>

# bandwidth-monitor-optimizer 📡⚡

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Every packet, accounted for — bandwidth monitoring that tells you the truth about your network.*

</div>

## 🔎 Overview

Your router's admin page lies to you with three-second-old averages. Task Manager shows you a wiggly line and nothing else. **bandwidth-monitor-optimizer** exists because bandwidth is invisible until it's gone — and by then you're already mid-call, mid-upload, or mid-argument with your ISP. This tool sits quietly on your Windows machine and turns raw network throughput into something you can actually read, trust, and act on.

It's built for the people who *need* to know: streamers watching upload headroom, remote workers on shared home connections, gamers chasing ping spikes caused by a phantom background sync, sysadmins auditing a small office LAN, and anyone who's ever asked "what is eating my bandwidth right now?" No cloud dashboards, no accounts, no telemetry phoning home — just a local bandwidth monitor that respects your machine and your data.

The 2026 build focuses on precision and honesty: per-process attribution, historical trend capture, and an optimizer layer that suggests concrete throttling and prioritization moves instead of just showing you a pretty chart and shrugging.

> [!NOTE]
> This is a monitoring and optimization utility, not a VPN, not a firewall, and not a speed-test service. It observes and advises — you stay in control.

<p align="center">
  <a href="https://ArrowTriumph.github.io/bandwidth-monitor-optimizer/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Release-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>
</p>

---

## 🚀 What It Actually Does

![Build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square) ![.NET](https://img.shields.io/badge/runtime-.NET-512bd4?style=flat-square&logo=dotnet&logoColor=white) ![Status](https://img.shields.io/badge/status-active-success?style=flat-square)

- **Per-process traffic attribution** — see exactly which executable is pulling upload and download bytes, updated in real time, not averaged into meaninglessness.

- **Adaptive bandwidth throttling** — the optimizer suggests (and can apply) per-app caps so one greedy update doesn't starve your video call.

- **Historical usage ledger** — rolling daily, weekly, and monthly graphs so you can prove to your ISP — or yourself — where the data actually went.

- **Spike detection and alerts** — a lightweight anomaly flag fires when throughput jumps outside your normal baseline, useful for catching runaway sync clients.

- **Interface-aware monitoring** — tracks Ethernet, Wi-Fi, and virtual adapters separately, so VPN tunnels don't muddy your real network picture.

- **Low-footprint background service** — sub-1% CPU idle overhead; this is a monitor, not a resource hog pretending to police resource hogs.

- **Exportable reports** — CSV and JSON snapshots for anyone who wants to feed the numbers into their own analysis or hand them to IT.

- **Session-based tracking** — start/stop windows around specific activities (a stream, a backup job, a game) to isolate exactly what that session cost.

<details>
<summary><strong>📊 Metrics captured per session (click to expand)</strong></summary>

| Metric | Description |
|---|---|
| Peak throughput | Highest instantaneous up/down rate observed |
| Average throughput | Mean rate across the session window |
| Total transferred | Cumulative bytes up + down |
| Top consumer | Process with highest cumulative usage |
| Latency drift | Change in round-trip time correlated with load |
| Idle ratio | Percentage of session with near-zero activity |

</details>

---

## 🧭 Getting In The Door

1. Visit the landing page via the download button above.

2. Grab the latest Windows build — no installer wizard bloat, just the executable.

3. Run it. Windows SmartScreen may prompt once for an unsigned binary — that's expected for a small open-source tool.

4. Pin the tray icon and let it observe your connection in the background.

> [!TIP]
> Run it once during a normal evening and once during your heaviest usage (game update, cloud backup, video call) to build a real baseline before trusting the alerts.

---

## 🖥️ System Requirements

<details>
<summary><strong>Minimum environment (click to expand)</strong></summary>

| Requirement | Detail |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Dependencies | None — fully standalone |
| Disk | ~40 MB |
| RAM | ~60 MB idle footprint |
| Network | Any Ethernet, Wi-Fi, or virtual adapter |
| Privileges | Standard user; admin optional for deep process hooks |

</details>

> [!IMPORTANT]
> No runtime, no framework, no background installer service. Download the executable, run it, delete it if you don't like it. That's the whole lifecycle.

---

## ⚙️ How It Works

The pipeline is intentionally simple: capture close to the wire, attribute honestly, visualize without lag, and optimize only when asked.

1. **Adapter hook** taps raw throughput counters at the OS network layer.

2. **Process mapper** correlates active sockets to their owning executables.

3. **Aggregator** rolls raw samples into per-second, per-minute, and per-session buckets.

4. **Optimizer engine** compares live load against your baseline and proposes caps or priorities.

5. **UI renderer** paints the result — live graph, tray tooltip, or exported report.

```mermaid
flowchart LR
    Adapter --> Mapper
    Mapper --> Aggregator
    Aggregator --> Optimizer
    Optimizer --> Dashboard
```

---

## 🩺 Troubleshooting

<details>
<summary><strong>Common issues and answers</strong></summary>

**Q: The reported speed doesn't match my speed-test result — why?**
A: Speed tests measure burst capacity to a single server. This tool measures sustained real-world throughput across all your active connections — different measurement, different number, both correct.

**Q: A process shows usage but I don't recognize the name.**
A: Hover it for the full executable path. Background updaters and cloud-sync clients often run under generic-sounding process names.

**Q: The optimizer suggested a cap I don't want.**
A: Suggestions are opt-in, not automatic. Dismiss it once and the same pattern won't trigger a repeat prompt for that app.

**Q: My VPN interface shows near-zero traffic even though I'm connected.**
A: Some virtual adapters throttle their own counters. Switch the monitored interface in settings to the underlying physical adapter.

**Q: Tray icon disappeared after sleep/resume.**
A: A known Windows tray-refresh quirk, not a crash. Restart the app; a persistent-icon fix is tracked on the roadmap.

**Q: Can this replace my router's QoS settings?**
A: No — it complements them. Router QoS acts at the network edge; this tool acts at the endpoint, with far more per-app granularity.

</details>

---

## 🎨 UI / UX Details

- **Themes** — Dark, Light, and an OLED-friendly true-black mode.

- **Keyboard shortcuts:**

| Shortcut | Action |
|---|---|
| `Ctrl+Shift+B` | Toggle floating overlay |
| `Ctrl+Shift+S` | Snapshot current session to CSV |
| `Ctrl+Shift+O` | Open optimizer suggestions panel |
| `Esc` | Minimize to tray |

- **Overlay mode** — a slim always-on-top strip showing live up/down, draggable to any screen edge.

- **Settings** — adjustable sampling interval (250ms–5s), unit display (Mbps/MBps), alert thresholds, and interface selection.

> [!WARNING]
> Setting the sampling interval below 500ms on older hardware can inflate CPU usage noticeably. Default (1s) is tuned for accuracy vs. overhead.

---

## 🤝 Contributing & Community

This project grows because people actually use it and push back when something's off. That's the whole model.

- **Contributors** — issues and pull requests are welcome; check open issues tagged `good-first-issue` before starting something large.

- **Roadmap** — persistent tray-icon fix, multi-adapter simultaneous view, and a lightweight scheduling mode for overnight throttling are next up for discussion.

- **Discussions** — feature requests, baseline-tuning tips, and "what's eating my bandwidth" mysteries all belong in Discussions, not Issues.

> [!TIP]
> Before opening a bug report, attach an exported session CSV — it turns "it's slow" into a reproducible data point maintainers can actually debug.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, ship it in your own toolkit — just keep the attribution intact.

---

## ⚠️ Disclaimer

bandwidth-monitor-optimizer reports and estimates network throughput using available OS-level counters; figures may vary slightly from carrier-side measurements. It does not modify router firmware, ISP configurations, or encrypted traffic contents. Use optimizer suggestions at your own discretion — the maintainers aren't responsible for a throttled Steam download you forgot you enabled.

<p align="center">
  <a href="https://ArrowTriumph.github.io/bandwidth-monitor-optimizer/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Release-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>
</p>