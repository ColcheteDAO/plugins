# 🎬 TikTokRetentionPlugin — Ultimate Interactive TikTok Live Challenge

[![Release Version](https://img.shields.io/badge/Release-v1.0.47-brightgreen.svg)](#)
[![Minecraft Version](https://img.shields.io/badge/Minecraft-1.20%20--%201.21+-blue.svg)](#)
[![Server Platforms](https://img.shields.io/badge/Supported-Paper%20%7C%20Spigot%20%7C%20Purpur-orange.svg)](#)
[![Java Runtime](https://img.shields.io/badge/Java-17%2B-red.svg)](#)
[![Zero Lag](https://img.shields.io/badge/Performance-Zero%20Lag%20Async-teal.svg)](#)

> **Transform your TikTok Live into an adrenaline-pumping Minecraft survival challenge!**  
> Keep your viewers glued to the screen, boost watch time, incentivize gifts and likes, and let your TikTok audience directly control the game in real time.

---

## 🌟 Overview

**TikTokRetentionPlugin** is a server-side Minecraft plugin crafted specifically for live streamers on TikTok. It turns the classic *"If my stream drops below X viewers, the world ends"* challenge into a fully automated, customizable in-game experience.

Gone are the days of manual monitoring or clumsy external setups. TikTokRetentionPlugin features **direct native TikTok Live polling** (no Python or Node scripts required), dynamic on-screen action bars, custom tab list leaderboards, coin and gift time multipliers, milestone rewards for stream likes, and brutal loss sequences when viewer thresholds aren't maintained.

---

## ⚡ Key Highlights

* **🎮 3-Phase Challenge Engine:** Automated Grace Period ➡️ Continuous Viewer Monitoring ➡️ Sudden Death Countdown with instant recovery.
* **📡 Direct TikTok Connection:** Input your `@username` directly in-game—no external dependencies or third-party bots required!
* **🎁 Gift & Coin Multipliers:** Every TikTok coin or gift sent adds precious seconds to your countdown timer, incentivizing viewers to support the stream.
* **❤️ Stream Likes Engine:** Reward stream activity! Every 1,000 stream likes adds bonus survival time.
* **🏆 Live Likers Leaderboard:** Track the top stream supporters in real time on both the Tab List and with in-game `/rank` commands.
* **💬 Dual-Chat Trigger Support:** Viewers on TikTok or players in Minecraft chat can type `rank`, `ranking`, or `likes` to broadcast the current top supporters.
* **📊 Seamless HUD & Action Bar:** Clean, flicker-free action bar displays current phase, remaining time, and viewer progress.
* **💀 Dramatic Elimination Sequence:** Clears inventory, switches to Spectator, and blasts a cinematic full-screen "YOU LOSE" title if the timer expires.
* **🚀 High-Performance & Asynchronous:** All network requests and calculations run completely off the main server thread to guarantee a solid 20.0 TPS.

---

## 🕹️ Challenge Flow & Mechanics

```
┌─────────────────────────────────────────────────────────────┐
│                   PHASE 1: GRACE PERIOD                     │
│  Default: 30 Minutes. Streamer gathers audience.            │
│  Viewers, gifts, and likes accumulate time.                 │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│               PHASE 2: RETENTION MONITORING                 │
│  Requires Target Viewers (e.g., 10+ simultaneous viewers).  │
│  If viewer count stays above target: All is safe!           │
└──────────────────────────────┬──────────────────────────────┘
                               │ Viewers drop below target
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                  PHASE 3: SUDDEN DEATH                      │
│  Default: 5-Minute emergency countdown!                     │
│  Action Bar flashes CRITICAL alerts.                        │
│  • Viewers recover above threshold ➔ RESETS to Monitoring!  │
│  • Timer reaches 0:00 ➔ DEFEAT SEQUENCE!                    │
└─────────────────────────────────────────────────────────────┘
```

### 1. Phase 1: Grace Period
When you join or start the stream, a configurable grace timer begins (default: 30 minutes). During this time, the streamer has full freedom to gather their audience without risk of immediate elimination. Coins and likes received during this phase add bonus time directly to your reserve.

### 2. Phase 2: Live Viewer Monitoring
Once the grace period concludes, the plugin actively monitors your live TikTok stream viewers. As long as concurrent viewers meet or exceed the target threshold (default: 10 viewers), the game remains in peaceful monitoring mode.

### 3. Phase 3: Sudden Death & Recovery
If your live viewer count dips below the required threshold, the plugin immediately triggers an emergency **Sudden Death** countdown (default: 5 minutes):
* **Live Action Bar Warning:** `CRITICAL! Time: 04:32 | Viewers: 7/10`
* **Recovery Mechanism:** If your viewers rally and push the count back to or above the threshold before the clock strikes zero, the countdown resets and returns to safe monitoring!

### 4. Defeat / Loss Sequence
If the timer runs out before the viewer count recovers:
* Full-screen red title: **YOU LOSE — Not enough visualizations!**
* Player inventory is wiped clean.
* Gamemode switches to `SPECTATOR`.
* Challenge enters paused/loss state.

---

## 💎 Interactive Viewer Engagement

### 🪙 Coins & Gifts
Reward viewers who support your stream. Every TikTok coin sent automatically adds survival time:
* Configurable rate (default: `+10 seconds` per coin).
* In-game chat broadcast announcing the gifter and added time.
* Track total coins earned and total seconds accumulated with `/ttr coins`.

### ❤️ Likes Milestones & Ranking
Turn tapping into a game mechanic:
* Configurable milestone: Every 1,000 stream likes adds configurable survival time (default: `+60 seconds`).
* In-game Tab List displays the **Top 5 Stream Likers** in real time.
* Run `/rank` or `/likes` in Minecraft chat to check the leaderboard.
* Anyone in Minecraft chat or TikTok live chat can trigger the leaderboard by saying `rank`, `ranking`, or `likes`.

---

## 💻 Commands & Permissions

### Commands Overview (`/ttr`, `/tiktokretention`, `/ag`)

| Command | Permission | Description |
| :--- | :--- | :--- |
| `/ttr start [username]` | `tiktokretention.admin` | Starts the challenge (optionally sets TikTok `@username`). |
| `/ttr stop` | `tiktokretention.admin` | Stops active challenge timers and resets phase. |
| `/ttr pause` | `tiktokretention.admin` | Pauses the active timer. |
| `/ttr resume` | `tiktokretention.admin` | Resumes a paused challenge timer. |
| `/ttr setusername <username>` | `tiktokretention.admin` | Sets your TikTok handle (e.g. `/ttr setusername @streamer`). |
| `/ttr setviewers <amount>` | `tiktokretention.admin` | Manually overrides viewer count (useful for testing). |
| `/ttr addcoins <amount>` | `tiktokretention.admin` | Simulates receiving TikTok coins and adds time. |
| `/ttr setcoins <amount>` | `tiktokretention.admin` | Overrides total coins received counter. |
| `/ttr addlikes <amount>` | `tiktokretention.admin` | Simulates or awards stream likes. |
| `/ttr setlikes <amount>` | `tiktokretention.admin` | Overrides total stream likes counter. |
| `/ttr coins` | `tiktokretention.user` | Displays total coins received and total time added. |
| `/ttr likes` | `tiktokretention.user` | Displays current top stream likers and total likes. |
| `/ttr rank [broadcast]` | `tiktokretention.user` | Displays stream likes leaderboard (add `broadcast` to show all). |
| `/ttr timer <show\|hide>` | `tiktokretention.admin` | Toggles or hides the on-screen countdown timer. |
| `/ttr hud <show\|hide>` | `tiktokretention.admin` | Controls whether action bar HUD is visible. |
| `/ttr addtime <seconds>` | `tiktokretention.admin` | Adds or removes time from the current phase timer. |
| `/ttr reset` | `tiktokretention.admin` | Resets current active phase timer to full duration. |
| `/ttr status` | `tiktokretention.user` | Displays stream handle, phase, timer, viewers, and metrics. |
| `/ttr verbose` | `tiktokretention.admin` | Toggles chat announcement verbosity. |
| `/ttr reload` | `tiktokretention.admin` | Reloads `config.yml` without server restart. |

### Standalone Leaderboard Commands
* `/rank [broadcast]` — View top TikTok live stream likers (aliases: `/likerank`, `/top`).
* `/likes` — Quick shortcut to view total likes and top supporters.

### Permissions

| Permission Node | Default | Description |
| :--- | :--- | :--- |
| `tiktokretention.admin` | `op` | Full access to start, stop, adjust, and configure the challenge. |
| `tiktokretention.user` | `true` | Allows players to view status, coins, and like rankings. |
| `antigravity.admin` | `op` | Compatibility alias for admin functionality. |

---

## ⚙️ Configuration Reference (`config.yml`)

The plugin comes with an extensively documented configuration file:

```yaml
# =============================================================
# TikTok Retention Plugin Configuration
# =============================================================

tiktok:
  # Your TikTok username (e.g. "@streamer" or "streamer")
  username: "your_tiktok_username"
  
  # Optional: TikTok sessionid cookie for authenticated live metric fetching
  session_id: ""
  
  # Enable direct plugin-side live stream polling (no external Python needed)
  enabled: true
  
  # How often the plugin queries TikTok for viewer counts (in seconds)
  poll_interval: 10

timers:
  # Automatically start the grace timer when a player logs in or plugin loads
  auto_start: true
  
  # Initial Grace Period duration (in minutes)
  initial_start_time: 30
  
  # Sudden Death countdown duration before loss (in minutes)
  punishment_countdown: 5
  
  # Interval for chat timer reminders (in seconds)
  chat_broadcast_interval: 60
  
  # Seconds added to current timer per coin received from gifts
  seconds_per_coin: 10
  
  # Whether the timer is displayed on screen HUD / action bar
  display_timer: true
  
  # Completely hide the action bar when timer is hidden (true) or show viewers only (false)
  hide_action_bar_when_hidden: true

thresholds:
  # Minimum simultaneous viewers required to stay in Monitoring phase
  minimum_visualizations: 10

messages:
  prefix: "&8[&bTikTok Retention&8] &r"
  verbose: true
  welcome: "&aWelcome to the server! TikTok Retention Plugin v%version% is active."
  welcome_enable: "&aTikTok Retention Plugin v%version% has been started!"
  send_welcome_on_join: true
  send_welcome_on_enable: true
  grace_period_time: "&aGrace period time remaining: &e%time%"
  countdown_time: "&cCRITICAL! Viewers are low! Time remaining: &e%time%"
  coins_received: "&aReceived &e%coins% TikTok Live coins&a! Added &e%time% &ato the timer."
  likes_received: "&aReached &e%likes% TikTok Live likes&a! Added &e%time% &ato the timer."
  action_bar_grace: "&aGrace Time: &e%time% &7| &aViewers: &e%viewers%/%required%"
  action_bar_sudden_death: "&c&lCRITICAL! &cTime: &e%time% &7| &cViewers: &e%viewers%/%required%"
  action_bar_monitoring: "&bStatus: Monitoring &7| &aViewers: &e%viewers%/%required%"
  lose_title_main: "&4&lYOU LOSE"
  lose_title_sub: "&cNot enough visualizations!"

api:
  # Embedded HTTP/WebSocket listener port for external bridge integrations
  websocket_port: 8080

likes:
  # Enable displaying top stream likers ranking on Tab List (header/footer)
  tab_list_enabled: true
  # Number of top likers to show on Tab List
  tab_top_limit: 5
  # Seconds added to timer per 1,000 stream likes
  seconds_per_1k_likes: 60
  # Threshold step for likes timer additions
  likes_threshold_step: 1000
```

---

## 🛠️ Installation & Setup (Under 2 Minutes)

1. **Download & Place:**  
   Download `TikTokRetentionPlugin-1.0.47.jar` and drop it into your server's `plugins/` directory.
2. **Start Server:**  
   Start or restart your Minecraft server (Paper or Spigot 1.20+).
3. **Configure Handle:**  
   In-game, run:
   ```
   /ttr setusername @your_tiktok_handle
   ```
   *(Or edit `plugins/TikTokRetentionPlugin/config.yml` and run `/ttr reload`)*.
4. **Start Stream & Play:**  
   Launch your TikTok Live, run `/ttr start`, and let the retention challenge begin!

---

## 🔌 Developer & External Bridge API

For creators who use external tools (such as custom Python `TikTokLive` connector scripts or Node.js bots), TikTokRetentionPlugin embeds an asynchronous lightweight HTTP listener on port `8080` (configurable in `config.yml`).

### HTTP Endpoints

* **`POST /viewers`** or **`POST /visualizations`**  
  Update live viewer count:
  ```json
  { "viewers": 24 }
  ```
* **`POST /coins`** or **`POST /gift`**  
  Inject gifts and trigger coin bonus time:
  ```json
  { "coins": 50, "giftName": "Rose" }
  ```
* **`POST /likes`**  
  Inject stream likes and liker names:
  ```json
  { "likes": 1500, "username": "SuperFan99" }
  ```
* **`POST /comment`**  
  Forward TikTok live comments for in-game triggers:
  ```json
  { "username": "ViewerOne", "comment": "rank" }
  ```
* **`GET /status`**  
  Returns JSON metadata of the current game phase, timers, and metrics.

---

## 📋 Compatibility & Requirements

| Component | Minimum Requirement | Recommended |
| :--- | :--- | :--- |
| **Server Software** | Spigot / Paper / Purpur 1.20 | PaperMC 1.20.4, 1.20.6, 1.21+ |
| **Java Version** | Java 17 | Java 21 |
| **Network** | Outbound HTTPS access to TikTok | High-speed connection |
| **Client** | Vanilla Minecraft 1.20+ | Any 1.20+ client |

---

## 💬 Support & Contributions

Have questions, suggestions, or need assistance setting up your live stream challenge?  
Feel free to open an issue or pull request on the official repository.
