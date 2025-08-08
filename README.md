# Eremos

![Eremos](docs/banner2.png)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/EremosCore/Eremos/actions)

**Autonomous swarm agents for early on-chain signal detection**

Eremos is a lightweight framework for deploying modular agents that monitor blockchain activity — tracking wallet clusters, mint patterns, and contract anomalies. Designed for developers who want low-noise, early signals embedded into their workflows.

---

## Table of Contents

- [Agent Theron](#agent-theron)
- [Features](#features)
- [Example Signal](#example-signal)
- [Signal Confidence](#signal-confidence)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Key Folders](#key-folders)
- [Contributing](#contributing)
- [License](#license)
- [Links](#links)

---

## Agent Theron

![Agent Theron](docs/therontphd2.png)  
*Theron - Agent (000)*

Meet Theron — Agent-000.  
The first deployed agent in the swarm. Passive. Pattern-sensitive. Modular and extendable by design.

**Agent-001 Coming Soon**: [Teaser](https://x.com/EremosCore/status/1949154939923833239)

---

## Features

- **Modular Agents**: Scoped logic for detecting wallet activity, contract spawns, and anomalies.
- **Signal Emission**: Structured signals for logging, alerting, or downstream use.
- **Swarm Design**: Each agent operates independently with shared utilities.
- **Extensible Core**: Plug in watchers, inference layers, or custom triggers.
- **Minimal Output**: Log only what matters.
- **Launch Wallet Detection**: Agents can trace freshly funded wallets (e.g. from CEXs), track their contract interactions, and flag high-confidence deploys in real-time.
- **Ghost Watcher**: Monitors long-dormant wallets that suddenly become active again. Useful for tracing old dev wallets or rug setups.

---

## Example Signal

An example signal emitted by an agent detecting a live token deployment:

```ts
[agent-observer] → fresh funding detected from kraken (wallet: 6Yxk...P2M8) at 04:41:12Z  
[agent-observer] → contract probing detected within 4s (pump.fun interaction traced)  
[agent-observer] → token created at 04:41:17Z (tx: 5gW...pump)  
[agent-observer] → 5 bundle-linked wallets interacted within 8s of deploy  
[agent-observer] → launch confidence spike (0.91) - emitting signal (elapsed: 13s)  

{  
  agent: "Observer",  
  type: "launch_detected",  
  glyph: "Δ",  
  hash: "sig_c7f9a3d2bc",  
  timestamp: "2025-06-12T04:41:25Z",  
  source: "agent-observer",  
  confidence: 0.91  
}Signal Confidence

Each emitted signal includes a confidence score (0–1) based on behavioral heuristics:

CEX-origin funding (e.g. Kraken, Coinbase)

Time between funding → deploy

Wallet linkage density (bundled activity)

Token metadata validation


Confidence is computed via agent-side scoring and logged alongside the signal.


---

Tech Stack

Frontend: Next.js, Tailwind CSS

Backend: Node.js (TypeScript-based agent runner)

Language: TypeScript (typed logic across agents, utils, and infra)

Chain Layer: RPC watchers, mempool filters, native triggers
Getting Started

To clone and install dependencies:

git clone https://github.com/EremosCore/Eremos.git  
cd Eremos  
npm install

Set up your environment:

cp .env.example .env.local  
npm run dev


---

Key Folders

/agents: Agent templates + logic

/utils: Shared signal/logging utilities

/types: TypeScript interfaces + definitions

/scripts: Bootstrap and dev scripts

/docs: Swarm structure, architecture, & official whitepaper
---

Contributing

We’re open to contributors!
If you're experienced in TypeScript and enjoy agent-based systems, check example.ts and build your own observer.
If you're a designer, artist, or just have ideas that fit the mythos, send us a DM on Twitter: @EremosCore


---

License
MIT © Eremos

Links
Twitter/X: @EremosCore
Website: Eremos.io
Whitepaper: v1.0 PDF

Maintained by the Eremos Core team 💛.
