# ⚔️ Vote Battle: Arena Edition 🏰
### *Interactive Team Sand Tower & TNT Airstrike Battle for PaperMC 1.21+*

![Tested Version](https://img.shields.io/badge/Minecraft-Paper%201.21%2B-blue?style=for-the-badge&logo=minecraft)
![Java Version](https://img.shields.io/badge/Java-21%20%2F%2026%2B-orange?style=for-the-badge&logo=openjdk)
![Platform](https://img.shields.io/badge/Crossplay-Java%20%26%20Bedrock%20(Geyser)-green?style=for-the-badge)
![Category](https://img.shields.io/badge/Type-TikTok%20Live%20%26%20Multiplayer%20Interactive-purple?style=for-the-badge)
![Developer](https://img.shields.io/badge/Author-ColcheteDAO-red?style=for-the-badge)

---

## 📖 Overview

**Vote Battle** is a high-octane, interactive Minecraft mini-game and live-streaming plugin engineered from the ground up for **PaperMC 1.21+** (fully optimized for Java 21 through Java 26+).

The game splits participants into two rival factions: **Red Team** and **Blue Team**. Players and live stream viewers compete in a dual-front war:
1. **Building their team's Sand Tower** by casting votes, likes, or comments to add sand blocks vertically.
2. **Bombing the opponent's Tower** with precision TNT airstrikes to blast away their sand layers and sabotage their progress!

Whether deployed on a multiplayer event server or integrated with **TikTok Live**, **YouTube Live**, or **Twitch** interactive stream tools, **Vote Battle** delivers thrilling tug-of-war gameplay, zero-lag block physics, dynamic HUDs, and bulletproof arena protection.

---

## ✨ Key Features & Architecture

### 🔴 1. Dynamic Teams & Chat Join System
- **Chat-Based Faction Enrollment**: Players in Minecraft chat can effortlessly join either team by typing standard trigger messages:
  - **Red Team**: `!red`, `#red`, `!vermelho`, or `!join red`
  - **Blue Team**: `!blue`, `#blue`, `!azul`, or `!join blue`
- **Console & Viewer Assignment**: External bots or admins can assign viewers or players using `/vb join <red|blue> [username]`.
- **Adventure MiniMessage Visuals**:
  - Red Team: `<gradient:#f87171:#dc2626><b>[RED]</b></gradient>`
  - Blue Team: `<gradient:#60a5fa:#2563eb><b>[BLUE]</b></gradient>`
- **Chat Formatting**: Custom chat renderer prefixes player messages with their active team badge.

### ⏳ 2. Sand Tower Physics & The "Like" Mechanic
- **Tower Progression & Random Falling**: When a like is credited to a player/viewer (e.g. via `/like <player/viewer> [amount]`, `/vb like <player/viewer> [amount]`, or HTTP `/api/like`), sand blocks fall **randomly across the base platform**, creating dynamic and organic mounds of sand!
  - **Auto-Assign Team**: If the user giving a like has no team assigned yet, they are automatically assigned to a balanced team (team with fewer members, or randomly tie-broken) so their like immediately adds sand!
- **Dynamic Physics & Staggered Drops**:
  - Drops falling sand blocks directly above randomly chosen `(X, Z)` positions across the base.
  - Multi-like barrages (e.g. `/like user 5`) are smoothly staggered with a 2-tick interval, raining sand down sequentially onto different parts of the base!
  - Guaranteed Solidification: A foundation check and 15-tick solidifier failsafe ensures every falling sand block lands securely and is never lost or destroyed.
- **Footprint Flexibility**:
  - `size: 1`: Single vertical pillar (1x1 classic sand column race).
  - `size: 3`: 3x3 platform footprint with randomized sand drop points.
  - `size: 5+`: Large expandable multi-block fortress towers.
- **Contributor Tracking**: Records the exact number of likes and sand blocks contributed by each player/viewer for live MVP rankings.

### 💣 3. TNT Opponent Tower Airstrikes
- **Direct Airstrike Dispatch**:
  - Players or viewers can bomb the opposing tower using `/tnt <username|team|opponent> [amount] [username]` or `/vb tnt ...`.
  - When passing a username (e.g. `/tnt Notch 5`), the plugin automatically looks up that user's team, targets their opponent's tower, and credits that user with the attacks for MVP leaderboards.
  - Console and external stream integrations can easily dispatch gifts directly: `/tnt <viewerName> [amount]` or `/tnt <team> [amount] <viewerName>`.
- **Smooth Staggered Barrages**: High-volume TNT requests are staggered with tick intervals to produce a realistic aerial bombardment instead of chaotic entity collision.
- **🛡️ 100% Guaranteed Arena Protection**:
  - All Vote Battle TNT entities are tagged with custom `PersistentDataContainer` (PDC) metadata.
  - An intelligent explosion filter (`ExplosionListener`) intercepts the explosion:
    - **Tower Sand**: Destroyed, removing layers from the opponent's tower and subtracting from their height.
    - **Arena Map, Bedrock, Floor, and Builds**: Completely immune to blast damage! Not a single floor block or arena structure will be harmed.
- **Visual & Audio Feedback**:
  - `ENTITY_TNT_PRIMED` and `ENTITY_WITHER_SPAWN` warning sound.
  - Immediate red title alert on the screens of all players on the targeted team: `⚠ INCOMING TNT! ⚠`.
  - Smoke vortex and blast particle effects upon impact.

### 🏆 4. Match Lifecycle, Win Tracking & Auto-Rounds
- **State Engine**: Managed across states `WAITING`, `STARTING`, `IN_PROGRESS`, and `ENDED`.
- **Win Condition A (Height Goal)**: The first team whose tower reaches the target height (default: 50m) instantly triggers round victory.
- **Win Condition B (Time Limit)**: If the round timer expires (default: 5 minutes), the team with the highest tower / most sand is crowned champion.
- **Persistent Win Tracking**: Win counters (`[X Wins]`) are recorded for Red and Blue factions across rounds.
- **Automatic Consecutive Rounds**:
  - Once time expires or a team wins, an auto-restart countdown begins (default: 10s cooldown for celebration & stats review).
  - Automatically resets towers, updates round numbers, and starts the next round seamlessly without admin intervention!
  - Can be toggled on/off on the fly with `/vb autostart [on|off]`.
- **Celebration Ceremony**:
  - Colored firework barrages launched directly from the winning tower's summit.
  - Full-screen gold victory title and fanfare (`UI_TOAST_CHALLENGE_COMPLETE`).
  - Match MVP summary broadcasting the top 3 Likers and top 3 Bombers.

### 📊 5. Live Stream HUD & Broadcast Interface
- **Dual-Colored Adventure BossBar**:
  - Displays dynamic tug-of-war balance with live wins: `RED [2W]: 24m ⚔ BLUE [1W]: 18m ★ Goal: 50m`.
  - Progress bar dynamically shifts towards the leading team.
- **Sidebar Scoreboard (15-Line Live Stream Display)**:
  - Match Timer & Current Round (`Time: 04:32 | R#3` or `Next Round: 7s`).
  - Team Wins Summary (`Wins: 2 - 1`).
  - Red Team: Tower Height, Sand Count, Members, and Win Badge (`[2W]`).
  - Blue Team: Tower Height, Sand Count, Members, and Win Badge (`[1W]`).
  - **Live In-Game Leaderboard (`★ LEADERBOARD ★`)**: Real-time Top 3 contributors ranking (colored by team, with total contribution points).
  - Target height goal marker & game state.

### 🌐 6. Built-in Zero-Overhead HTTP REST Bridge
- Runs an embedded HTTP server (default port `8085`) using standard Java runtime APIs with zero external dependencies:
  - `POST /api/like`: `{"user": "ViewerName", "amount": 5}` (adds 5 sand to viewer's team tower).
  - `POST /api/tnt`: `{"target": "blue", "amount": 2, "attacker": "ViewerName"}` (launches 2 TNT at Blue tower).
  - `POST /api/join`: `{"user": "ViewerName", "team": "red"}` (joins Red team).
  - `GET /api/status`: Returns JSON snapshot of current game state, scores, and heights.
- Ready for Python TikTokLive connectors, Stream Deck buttons, and web overlays.

---

## 🕹️ Command Reference

### Player & Viewer Commands:
| Command | Aliases | Description |
| :--- | :--- | :--- |
| `/join <team> [username]` | — | Join a team or register/assign a specific username into a team. |
| `/like <player/viewer> [amount]` | — | Add sand block(s) to a player's team tower. |
| `/tnt <username\|team\|opponent> [amount] [username]` | — | Launch primed TNT airstrike onto opponent tower (or target opponent of specified user). |

### Chat Triggers:
- Type `!red`, `#red`, or `!join red` in Minecraft chat to join Team Red.
- Type `!blue`, `#blue`, or `!join blue` in Minecraft chat to join Team Blue.
- If a custom match is active (e.g. Lions vs Tigers), type `!Lions` or `!Tigers` to join that team!

### Administrative Commands (`/votebattle` or `/vb`):
| Command | Permission | Description |
| :--- | :--- | :--- |
| `/vb join <team> [username]` | `votebattle.player` | Join team or assign a player/viewer into that team. |
| `/vb match <team1> <team2>` | `votebattle.admin` | Create a new match with custom team names (e.g. `/vb match Lions Tigers`). |
| `/vb start [team1] [team2]` | `votebattle.admin` | Starts a new game, resetting win scores & leaderboard (optionally with custom teams). |
| `/vb setname <team> <name>` | `votebattle.admin` | Renames a team during or before a match. |
| `/vb settower <team> [size]` | `votebattle.admin` | Sets tower center base with custom size (e.g. `1` for 1x1, `3` for 3x3) and auto-deletes existing sand blocks. |
| `/vb setspawn <red\|blue>` | `votebattle.admin` | Sets the team spawn location. |
| `/vb buildbase [team|all] [size]` | `votebattle.admin` | Generates solid foundation platforms under towers with custom size (e.g. `/vb buildbase 3` or `/vb buildbase red 5`). |
| `/vb stop` | `votebattle.admin` | Stops the running match and cancels auto-restart. |
| `/vb reset [arena\|wins\|all]` | `votebattle.admin` | Clears tower sand, resets team wins, or resets entire session. |
| `/vb autostart [on\|off]` | `votebattle.admin` | Toggles automatic next round start when time finishes or match ends. |
| `/vb setwins <team> <amount>` | `votebattle.admin` | Manually sets the win counter for a team. |
| `/vb stats` | `votebattle.player` | Displays live tower heights, team win scores, and contributor leaderboard. |
| `/vb reload` | `votebattle.admin` | Reloads `config.yml` settings on the fly. |

---

## ⚙️ Configuration Reference (`config.yml`)

```yaml
# ==============================================================================
#                  Vote Battle - PaperMC Configuration
#                     Developed by ColcheteDAO
# ==============================================================================

# General Match & Win Condition Settings
game:
  # Duration of each match in seconds (e.g. 300 = 5 minutes)
  duration_seconds: 300
  # Automatically end match and declare victory when a tower reaches goal_height
  win_by_height: true
  # Seconds for match countdown
  countdown_seconds: 5
  # Automatically start another round when match time finishes or match ends
  auto_start_next_round: true
  # Seconds to wait between rounds before auto-starting the countdown
  auto_start_delay_seconds: 10
  # Automatically teleport players to team spawn points on match start (false = keep players where they are)
  teleport_players_on_start: false

# Teams Configuration
teams:
  red:
    display_name: "Red Team"
    tag: "<gradient:#f87171:#dc2626><b>[RED]</b></gradient>"
    sand_material: "RED_SAND" # Options: RED_SAND, RED_CONCRETE_POWDER, etc.
    tower:
      world: "world"
      x: 0.5
      y: 64.0
      z: -10.5
    spawn:
      world: "world"
      x: 0.5
      y: 65.0
      z: -15.5
      yaw: 0.0
      pitch: 0.0

  blue:
    display_name: "Blue Team"
    tag: "<gradient:#60a5fa:#2563eb><b>[BLUE]</b></gradient>"
    sand_material: "SAND" # Options: SAND, CYAN_CONCRETE_POWDER
    tower:
      world: "world"
      x: 0.5
      y: 64.0
      z: 10.5
    spawn:
      world: "world"
      x: 0.5
      y: 65.0
      z: 15.5
      yaw: 180.0
      pitch: 0.0

# Physical Tower Stacking Settings
tower:
  # Height (in blocks) needed to win the match immediately
  goal_height: 50
  # 0 = 1x1 vertical pillar; 1 = 3x3 footprint; 2 = 5x5 footprint
  radius: 0
  # If true, sand drops as dynamic falling blocks; if false, placed instantly
  falling_block_animation: true

# TNT Airstrike & Bombing Settings
tnt:
  # Fuse time in ticks (20 ticks = 1 second)
  fuse_ticks: 45
  # Height above tower where TNT spawns
  spawn_height_offset: 8
  # If false, destroyed sand vanishes cleanly without item entity clutter
  drop_items: false

# Arena & Environment Protection
arena:
  # Explosions CANNOT damage any world blocks outside of active tower sand
  protect_environment: true
  # Prevent unwanted player PVP in the arena
  pvp_disabled: true

# Minecraft Chat Interactions
chat:
  allow_chat_join: true
  allow_chat_like: false
  allow_chat_tnt: false
  format_with_team: true

# HUD & Visuals
hud:
  scoreboard:
    enabled: true
  bossbar:
    enabled: true

# HTTP REST Bridge (For TikTok Live, YouTube Live, Stream Deck)
http_bridge:
  enabled: true
  port: 8085
```

---

## 🚀 Setup & Arena Walkthrough

1. **Install Plugin**:
   - Place `VoteBattle-1.0.0.jar` into your server's `plugins/` directory.
   - Start or restart your server.

2. **Configure Tower Locations**:
   - Walk to where the **Red Tower** should stand and run:
     ```bash
     /vb settower red
     ```
   - Walk to where the **Blue Tower** should stand and run:
     ```bash
     /vb settower blue
     ```

3. **(Optional) Set Team Spawns & Platform**:
   - Stand at team spawn locations and run `/vb setspawn red` and `/vb setspawn blue`.
   - Run `/vb buildbases` to lay down concrete platform foundations.

4. **Join & Play**:
   - Players type `!red` or `!blue` in chat to join.
   - Start the game using:
     ```bash
     /vb start
     ```
   - Send likes (`/like <player> 1`) and bomb opponents (`/tnt blue 1`)!

---

## 🔒 Permissions

- `votebattle.admin` *(Default: OP)*: Full access to setup, arena reset, and match control.
- `votebattle.player` *(Default: true)*: Standard player permissions for `/join`, `/like`, `/tnt`, and `/vb stats`.

---

<p align="center">
  <b>Vote Battle — Engineered by ColcheteDAO</b><br>
  <i>PaperMC 1.21+ • Java 21-26+ Ready • Zero TPS Overhead • Pure Excitement</i>
</p>
