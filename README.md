<p align="center">
  <img src="https://img.shields.io/badge/STATUS-DEVELOPMENT%20SUSPENDED-8B0000?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/SUPPORT-DISCONTINUED-8B0000?style=for-the-badge" alt="Support">
  <img src="https://img.shields.io/badge/UPDATES-PAUSED-8B0000?style=for-the-badge" alt="Updates">
  <img src="https://img.shields.io/badge/DISTRIBUTION-PUBLIC%20JAR-555555?style=for-the-badge" alt="Distribution">
</p>

---

<h2 align="center"><code>PROJECT NOTICE — DEVELOPMENT SUSPENDED</code></h2>

<p align="center"><em>Effective immediately, this project has been placed on indefinite hold.</em></p>

---

**Reason for suspension.** Active development has been halted due to limited funding, insufficient development time, and the absence of a complete development team.

**Release version.** The build currently available under the **Releases** section is an **in-development (pre-release) version**, not a finalized production build. As such, a number of **minor, low-visibility features may not function as intended**. The core systems are stable, but small edge cases and secondary details were still being refined at the time development was paused.

**Current terms of the project.**

- Support is **no longer provided**.
- No further updates will be released.
- The compiled **JAR** of the latest build remains publicly available under the **Releases** section.
- The project may be downloaded and used in its current state, as-is.

**Regarding the source code.** Open-sourcing the source is **not possible** at this time due to licensing restrictions.

**Resumption of development.** Should a **sponsor or development team** come forward, development will resume immediately. For sponsorship or support inquiries, please contact the developer directly.

---

<h1 align="center">Anti-Cheat</h1>

<p align="center"><strong>The most precise simulation-based anticheat for Minecraft 1.8.8.</strong></p>

# Anti-Cheat

**Simulation-based anticheat for Minecraft 1.8.8, powered by PacketEvents 2.0.**
Engineered for networks that demand the most precise cheat detection available, with over 200 detection methods powered by a full client-side physics prediction engine.
Tailored for servers hosting more than 1,000 players, every check runs through exhaustive verification algorithms that replicate exactly what the vanilla client would do — so legitimate players are never false-flagged, and cheaters are caught with surgical accuracy.

---

## Table of Contents

- [Why Anti-Cheat?](#why-anti-cheat)
- [Competitive Comparison](#competitive-comparison)
- [Why Exclusively 1.8.8?](#why-exclusively-188)
- [Core Engine – Prediction-Based Detection](#core-engine--prediction-based-detection)
- [Combat Checks](#combat-checks)
- [Movement Checks](#movement-checks)
- [Scaffolding Checks](#scaffolding-checks)
- [Breaking Checks](#breaking-checks)
- [Bad Packet & Exploit Detection](#bad-packet--exploit-detection)
- [Sprint, Chat & Packet Order Checks](#sprint-chat--packet-order-checks)
- [Setback & Alert System](#setback--alert-system)
- [Punishment System](#punishment-system)
- [Data Storage Backends](#data-storage-backends)
- [Integrations](#integrations)
- [Commands & Permissions](#commands--permissions)
- [Frequently Asked Questions](#frequently-asked-questions)
- [Support & Purchasing](#support--purchasing)

---

## Why Anti-Cheat?

Anti-Cheat is not a pattern-matching script that flags anything that looks suspicious. It is a full simulation engine that predicts exactly where a player should be, what speed they should be moving, and what actions they should be able to perform — then verifies every single packet against that prediction.

### 200+ Detection Methods, Not 200 Regex Rules
Every check is built on a physics prediction engine that replicates client-side movement, gravity, friction, and input. When a player sends a packet, Anti-Cheat simulates what the vanilla client would have sent under the same conditions. If the actual packet deviates from the prediction, the player is flagged. This approach eliminates the false positives that plague pattern-based anticheats while catching sophisticated cheats that evade simple heuristic checks.

### Packet-Level Analysis with PacketEvents 2.0
Anti-Cheat does not rely on Bukkit events, which are processed after the server has already accepted the data. It intercepts packets at the lowest level using PacketEvents 2.0, analyzing raw movement, interaction, and transaction data before any server-side processing occurs. This means cheaters cannot exploit timing gaps between packet arrival and event dispatch.

### Built for Large Networks
Designed and stress-tested for servers with 1,000+ concurrent players. Redis handles session and setting storage for sub-millisecond access. Database operations run asynchronously. The alert system is rate-limited to prevent console spam during mass violation events. Auto-kick ensures high-confidence removal of players who accumulate violations across multiple check categories.

### Free, Public Release
The project is no longer sold. The latest compiled build is publicly available, free of charge, under the **Releases** section — covering every server you own, with no fees, no per-server charges, and no hidden costs.

### Direct Access to the Developer
When a cheater bypasses a check at peak time, you do not file a ticket and wait three days. You speak directly to the person who wrote the detection algorithm. However, note that active support is **no longer provided**, as development is currently suspended.

---

## Competitive Comparison

| Criteria | **Anti-Cheat** | Grim | NCP | Vulcan | Polar | Other "Premium" |
|----------|---------------|------|-----|--------|-------|----------------|
| **Detection methods** | 200+ (simulation-based) | ~100 | ~80 | ~120 | ~60 | Usually 30-60 |
| **Prediction engine** | Full client-side physics replication | Partial | No | Partial | No | Rare |
| **Packet library** | PacketEvents 2.0 | PacketEvents | NMS | Own | NMS | Usually NMS |
| **Combat checks** | Reach, Hitboxes, Self-Interact, Multi-Interact, Attack Cooldown | Basic | Basic | Good | Basic | Varies |
| **Movement checks** | Flight (prediction), Speed, Timer, Negative Timer, Tick Timer, NoFall, Ground Spoof, Phase, NoSlow, Vehicle | Basic | Moderate | Good | Basic | Varies |
| **Scaffolding checks** | Rotation, Position, Far, Fabricated, Air/Liquid, Invalid, Duplicate Rotation, Multi Place | Basic | Limited | Moderate | Limited | Rare |
| **Breaking checks** | Rotation, Position, Speed, Far, Wrong, Multi, No Swing, Air/Liquid, Invalid | Basic | Limited | Moderate | Limited | Rare |
| **Bad packets** | A through Z (26+ sub-checks) | Limited | Limited | Good | Limited | Varies |
| **Packet order checks** | Transaction suppression, Anti-KB bypass | No | No | Basic | No | Rare |
| **Storage backends** | SQLite, MySQL, PostgreSQL, MongoDB, Redis | MySQL/SQLite | Flat/MySQL | MySQL | MySQL | Usually MySQL only |
| **Discord webhooks** | Configurable embeds with rate limiting | No | Via addon | No | No | Rare |
| **Folia support** | Yes | Yes | No | Yes | No | Rare |
| **License model** | Free, public release | Free | Free | Paid | Free | Often per-server or recurring |

**Key takeaway:** Anti-Cheat is the only plugin that combines a full physics prediction engine, 200+ detection methods, 5 storage backends, and Discord webhook integration — in a single free public release.

---

## Why Exclusively 1.8.8?

Targeting 1.8.8 is an intentional engineering choice. The 1.8.8 PvP scene is where the most competitive players and the most sophisticated cheats exist. Building exclusively for this version means every detection algorithm is written directly against the 1.8.8 packet format, movement mechanics, and combat timing — with no compromises for cross-version compatibility.

1. **The competitive PvP standard.** The largest networks and the most competitive players operate on 1.8.8. Combat mechanics, knockback calculations, and block-hitting behaviour that competitive players demand are tied to this version.
2. **Maximum detection precision.** Writing for a single version means the prediction engine can use exact 1.8.8 friction values, gravity constants, and input handling — not approximations that must work across versions.
3. **No compromises.** Cross-version anticheats must abstract their checks to work on multiple packet formats. This abstraction creates blind spots that sophisticated cheats exploit. Anti-Cheat has no such blind spots.

---

## Core Engine – Prediction-Based Detection

Anti-Cheat uses a full prediction engine that replicates client-side physics:

- Simulates gravity, friction, and player input for every movement packet.
- Compares predicted position against actual reported position.
- Verifies attack timing, range, and aim against vanilla combat mechanics.
- Validates block placement and breaking against reach and rotation constraints.
- Supports both Folia and Paper server platforms.
- ViaVersion compatibility for cross-version servers.

---

## Combat Checks

| Check | Description |
|-------|-------------|
| **Reach** | Detects attacks beyond allowed range, including 1.21.11+ attack range component support |
| **Hitboxes** | Validates that the player is aiming at a valid part of the entity hitbox |
| **Self-Interact** | Prevents players from interacting with themselves |
| **Multi-Interact** | Detects impossible interaction patterns within a single tick |
| **Attack Cooldown** | Ensures players respect the vanilla attack cooldown timing |

---

## Movement Checks

| Check | Description |
|-------|-------------|
| **Flight** | Full prediction-based flight detection with gravity, friction, and input simulation |
| **Speed** | Detects horizontal movement exceeding vanilla limits |
| **Timer** | Identifies game tick rate manipulation (sending packets too fast) |
| **Negative Timer** | Detects reversed or negative tick timing exploits |
| **Tick Timer** | Additional tick-based timing analysis |
| **NoFall** | Detects players attempting to bypass fall damage |
| **Ground Spoof** | Identifies clients falsely reporting ground state |
| **Phase** | Prevents players from moving through solid blocks |
| **NoSlow** | Ensures slowness effects (soul sand, webs, items) are respected |
| **Vehicle Movement** | Full vehicle prediction and movement validation |

---

## Scaffolding Checks

| Check | Description |
|-------|-------------|
| **Rotation Place** | Validates block placement rotation accuracy |
| **Position Place** | Ensures blocks are placed within reachable positions |
| **Far Place** | Detects placement of blocks at impossible distances |
| **Fabricated Place** | Identifies fake or fabricated block placement data |
| **Air/Liquid Place** | Prevents placement in invalid mediums |
| **Invalid Place** | Detects placement that violates vanilla constraints |
| **Duplicate Rotation Place** | Catches rotation reuse exploits |
| **Multi Place** | Identifies multiple placements in a single tick |

---

## Breaking Checks

| Check | Description |
|-------|-------------|
| **Rotation Break** | Validates block breaking rotation accuracy |
| **Position Break** | Ensures blocks are broken within reachable positions |
| **Speed Break** | Detects breaking blocks too quickly |
| **Far Break** | Detects breaking blocks at impossible distances |
| **Wrong Break** | Prevents breaking blocks that cannot be broken |
| **Multi Break** | Identifies multiple block breaks in a single tick |
| **No Swing Break** | Ensures arm swing animation accompanies block breaks |
| **Air/Liquid Break** | Prevents breaking in invalid mediums |
| **Invalid Break** | Detects breaking that violates vanilla constraints |

---

## Bad Packet & Exploit Detection

Comprehensive packet validation across 26+ sub-checks (BadPackets A through Z) that detect invalid, out-of-order, or malformed packets sent by the client. Additionally prevents known game exploits and edge-case abuse vectors.

---

## Sprint, Chat & Packet Order Checks

- **Sprint Checks**: Detects sprint state desynchronization exploits and validates sprint toggling timing.
- **Chat Checks**: Pattern-based chat analysis across multiple sub-checks.
- **Packet Order Checks**: Validates packet ordering to detect transaction suppression and reordering exploits. Prevents Anti-KB bypass via transaction manipulation.

---

## Setback & Alert System

### Setback System
- Teleports players back to the last known valid position on violation.
- Configurable per-check setback behavior.
- Supports plugin-initiated and check-initiated setbacks.

### Alert System
- Real-time console alerts for staff members with the `anticheat.alerts` permission.
- Verbose mode providing detailed debug information per violation.
- Per-player alert toggles with optional enable-on-join.
- Discord webhook integration with configurable embeds, rate limiting, and retry logic.

---

## Punishment System

- Configurable punishment groups with check pattern matching.
- Threshold-based violation counting per check.
- Command execution on violation threshold reached.
- Configurable violation decay timer.
- Per-category punishment rules.
- Auto-kick system that removes players accumulating violations across multiple categories.

---

## Data Storage Backends

Hot-swappable backend configuration with automatic connection management:

| Backend | Use Case | Details |
|---------|----------|--------|
| **SQLite** | Default lightweight storage | No external dependencies, zero configuration |
| **MySQL** | Full relational database | HikariCP connection pool |
| **PostgreSQL** | Advanced relational database | Full feature support |
| **MongoDB** | Document-based storage | Flexible schemas |
| **Redis** | Session data & player settings | Default, sub-millisecond access |

---

## Integrations

| Integration | Description |
|-----------|-------------|
| **PlaceholderAPI** | Custom placeholders for violation counts, player data, and check status |
| **LuckPerms** | Permission-based exemption and context-aware resolution |
| **Discord Webhooks** | Configurable violation alerts with embeds, thumbnails, and rate limiting |
| **bStats** | Anonymous usage statistics |

---

## Commands & Permissions

| Command | Description | Permission |
|---------|-------------|------------|
| `/anticheat` | Display help information | `anticheat.help` |
| `/anticheat alerts` | Toggle alerts for the sender | `anticheat.alerts` |
| `/anticheat verbose` | Toggle verbose output | `anticheat.verbose` |
| `/anticheat brands` | Toggle client brand display | `anticheat.brand` |
| `/anticheat debug [player]` | Toggle debug output for a player | `anticheat.debug` |
| `/anticheat version` | Show current version | `anticheat.version` |
| `/anticheat reload` | Reload configuration | `anticheat.reload` |
| `/anticheat list` | Show lists of specific data | `anticheat.list` |

| Permission | Default | Description |
|------------|---------|-------------|
| `anticheat.alerts` | OP | Receive alerts for violations |
| `anticheat.alerts.enable-on-join` | OP | Enable alerts on join |
| `anticheat.brand` | OP | Show client brands on join |
| `anticheat.verbose` | OP | Receive verbose alerts |
| `anticheat.debug` | OP | Toggle debug output |
| `anticheat.reload` | OP | Reload configuration |
| `anticheat.exempt` | FALSE | Exempt from all checks |
| `anticheat.disabled` | FALSE | Disable checks while keeping player state tracked |
| `anticheat.nosetback` | FALSE | Disable setback |

---

## Frequently Asked Questions

### General Questions

**Q: Does Anti-Cheat work with ViaVersion?**
A: Yes. Anti-Cheat has full ViaVersion compatibility for cross-version servers.

**Q: How does the license work?**
A: No license is sold. The project has been suspended and the latest build is available free of charge under the **Releases** section.

**Q: Can I test the plugin?**
A: Yes. Connect to `mc.hypeland.org` to experience the plugin on a live server — no registration required.

### Technical Questions

**Q: What Java version does my server need?**
A: Java 21 or newer.

**Q: Does it support Folia?**
A: Yes. Anti-Cheat supports both Folia and Paper server platforms.

**Q: How many detection methods are there?**
A: Over 200 detection methods across combat, movement, scaffolding, breaking, bad packets, sprint, chat, and packet order checks.

**Q: What storage backend should I use?**
A: Redis is the default for session and settings data (sub-millisecond access). SQLite is the default for violation data. MySQL, PostgreSQL, and MongoDB are available for larger deployments. All backends are hot-swappable.

**Q: Does the auto-kick system ever false-positive?**
A: The auto-kick requires violations across multiple check categories (minimum 2 by default) and a high total violation threshold (100 by default). This ensures high confidence before any action is taken.

### Support

**Q: How do I get help if something breaks?**
A: Active support is **no longer provided**, as development is suspended. You may still contact the developer, but no official assistance is guaranteed.

**Q: Are updates free?**
A: No further updates are planned. The current build is the final public release.

---

## Support & Purchasing

**This project is no longer sold.** As stated in the Project Notice above, development has been suspended indefinitely and commercial distribution has been discontinued.

### How to Get the Plugin
The latest compiled **JAR** is publicly available, free of charge, under the **Releases** section of this repository. Download it, drop it into your `plugins/` folder, and use it as-is.

### No Purchase, No License Fee
There is no price, no license key, no loader, and no payment of any kind. The project is released publicly for anyone to use.

### Sponsorship & Resumption
If you are interested in **sponsoring this project** or joining a **development team** to resume it, please contact the developer directly. Sponsorship is the only path toward continued development.

### Contacts
- **Discord:** `Nerotek01`
- **Bale (Iranian users):** `Nerotek`
- **Demo server:** `mc.hypeland.org`

### Support
Active support is **no longer provided**, as development is suspended. The community may still discuss the plugin, but no official assistance is guaranteed.

---

<p align="center">
  <a href="https://mc.hypeland.org"><strong>Connect to the demo: mc.hypeland.org</strong></a>
</p>
