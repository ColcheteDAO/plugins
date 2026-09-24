# ✦ DuneFall: Laboratory Edition ✦
### *Interactive TikTok Live Stream Mini-Game & StreamTK Manager for PaperMC 1.21+*

![Tested Version](https://img.shields.io/badge/Minecraft-Paper%201.21%2B-blue?style=for-the-badge&logo=minecraft)
![Platform](https://img.shields.io/badge/Crossplay-Java%20%26%20Bedrock%20(Geyser)-green?style=for-the-badge)
![Category](https://img.shields.io/badge/Type-TikTok%20Live%20Interactive-purple?style=for-the-badge)

---

## ⚡ Overview

**DuneFall: Laboratory Edition** is a commercial-grade, turn-key Minecraft plugin engineered specifically for interactive **TikTok Live Streams**. It gamifies your live broadcasts by putting viewers in total control of the arena using **TikTok gifts** (integrated seamlessly via **StreamTK**, **SuperStream**, or any console automation bot).

The objective is simple yet addictive: the streamer must excavate and purge the arena platform before the countdown expires. Viewers can send gifts to summon avalanches of colored sand, strike the arena with lightning, drop primed TNT, trap the streamer in cages, or trigger massive platform purges!

Built from the ground up for **PaperMC 1.21+**, DuneFall delivers butter-smooth block physics with zero TPS drops, an evocative melancholic laboratory aesthetic, and deep in-stream player progression.

---

## 🔬 Key Features

### 🌟 1. Melancholic Laboratory Aesthetic
- **Adventure MiniMessage Gradients**: Crisp neon cyan, electric purple, and amber UI formatting.
- **Atmospheric Soundscape**: Custom auditory feedback utilizing beacon harmonics, sculk sensor frequencies, respawn anchor hums, and conduit activations.
- **Laboratory VFX**: Custom particle vortexes, soul flame bursts, and dimensional rift teleports.

### 🎮 2. Infinite Sand Physics & Auto-Expanding Arena
- **Realistic Sand Cascades**: Blocks collapse instantaneously with custom gravitational math that prevents entity clutter and client desync.
- **Dynamic Containment Perimeter**: As viewers pile up sand into towering columns, the laboratory glass containment walls automatically extend upward in real time.
- **Panic Evacuation Protocol (`/dunefall tp`)**: Streamer trapped or buried? One command scans the highest block stratum and safely teleports the streamer to safety.
- **17+ Chromatic Sand Colors**: Full support for standard sand, red sand, and 16 distinct colored concrete powders (or full chromatic rainbow randomizer).

### ⛏️ 3. 120-Level Equipment Evolution Engine
Forget about boring static tools! The streamer's shovel evolves **directly in their hand** as they excavate:
- **Level 1 – 9 (Wood Tier)**: Pioneer Wooden Shovel.
- **Level 10 – 19 (Cobblestone Tier)**: Automatically transmutes into Stone Shovel upon hitting Level 10; unlocks *Mending*!
- **Level 20 – 29 (Iron Tier)**: Transmutes into Iron; unlocks *Fire Aspect* on weapons.
- **Level 30 – 39 (Gold Tier)**: Transmutes into Gold; unlocks *Looting* and rapid mining speed.
- **Level 40 – 49 (Diamond Tier)**: Transmutes into Diamond; Tier V enchantments unlocked.
- **Level 50 – 120 (Netherite Master Tier)**: The legendary *Obsidian Excavator* with Efficiency X, Unbreaking X, Sharpness X, and Power X.
- **Dynamic Lore HUD**: Live ASCII progress bar (`[██████░░░░] 60%`), exact block breakdown stats, and next material ascension previews.
- **Cross-Discipline Progression**: Swords level up via combat strikes; bows level up through archery shots!

### 🛒 4. Laboratory Specimen Economy & Shop (`/shop`)
- **Earn Coins by Mining**: Earn specimen currency for every sand block broken.
- **Pioneer Gear**: The shop sells exclusively the baseline Tier I tool — no pay-to-skip; players must earn their transcensions!
- **Consignment Liquidation (`/sell`)**: Instantly liquidate entire inventories of excavated sand and loot for coins with differential stratum pricing.
  - *100% Protection Guarantee*: Shop-purchased items, armor, and progression tools are hard-protected and never sold by accident!
- **Tactical Stimulants**: Purchase speed sera, adrenaline boosts, stasis pearls, and emergency Totems of Undying.
- **Blast Protection Armor**: Tiered blast-shield armor sets engineered to withstand viewer TNT and lightning strikes.
- **Laboratory Mending Core (`/shop`)**: Purchase portable Mending Cores (350 coins) that can be applied to **ANY** armor, weapon, or tool via direct in-hand infusion or inventory drag-and-drop!
- **Continuous Auto-Repair Protocol & Repair Station (`/dunefall repair` & `/dunefall autorepair`)**:
  - Automatically heals equipment, weapons, and armor continuously by removing **2 coins per durability point**!
  - **Activation Threshold & Full Recovery**: Auto-repair engages automatically whenever any piece of equipment or armor in inventory falls **below 50 durability**, and stays active repairing all damaged gear **until ALL items in inventory are 100% fully recovered**!
  - Anvil station and `/dunefall repair` restore durability at **2 Coins per durability point** with partial repair support.

### 📊 5. TikTok-Optimized Stream HUD & Master Hide Switch
- **Lowered BossBar**: Specially positioned to prevent obstruction by TikTok's top viewer count, notifications, and LIVE badge.
- **Action Bar Purge Meter**: Real-time extraction percentage (`Purge: [████░░░░] 45.0% • Remaining: 120/400`).
- **Sidebar Scoreboard**: Real-time Game State, Countdown Timer, Stream Win/Loss Record (`12W - 3L`), Balance, and Top Live Gifter Leaderboard.
- **✦ Master HUD Hide Switch (`/hud` or `/dunefall hud`)**:
  - Instantly hide or restore all on-screen UI elements (Scoreboard, BossBar, and Action Bar) with a single command for clean camera angles, cinematic cuts, or personalized streaming layouts!

---

## 🎁 TikTok Gift Mappings (StreamTK / SuperStream)

DuneFall is designed for plug-and-play console automation. Configure your TikTok Live connector to dispatch these commands when viewers send gifts:

| TikTok Gift Example | Console Command Trigger | In-Game Action |
| :--- | :--- | :--- |
| 🌹 **Rose / Cap** | `dunefall lightning 1 {username}` | Dispatches a targeted lightning blast with controlled arena damage. |
| 💖 **Finger Heart** | `dunefall sand random cyan 10 {username}` | Drops 10 blocks of falling cyan concrete powder above the platform. |
| 🍩 **Doughnut / Heart** | `dunefall tntnear 1 {username}` | Safely spawns primed TNT near the player with fuse alerts. |
| 🥊 **Boxing Gloves** | `dunefall prison 8 {username}` | Encases the streamer in a Crying Obsidian & Iron Bar cage for 8s. |
| 🎆 **Fireworks** | `dunefall randomrow 1 {username}` | Injects an entire multi-colored row of falling sand across the arena. |
| ☕ **Coffee / GG** | `dunefall deleterow 1 {username}` | Removes 1 stratum from the bottom; upper sand collapses realistically. |
| 🌌 **Galaxy / Whale** | `dunefall fill {username}` | Floods the entire arena platform to maximum capacity with sand! |
| 🦁 **Lion / Universe** | `dunefall clear {username}` | Instantly purges all sand from the platform, awarding a round victory! |

*Note: All commands accept the viewer's username as an argument to automatically update the in-game Top Gifter Leaderboard on the sidebar!*

---

## ⌨️ Command Database

### Core Streamer & Arena Commands
- `/dunefall create [size] [height]` – Generate the arena platform and commence round.
- `/dunefall delete` – Eradicate the active arena and halt timers.
- `/dunefall reset` – Full administrative rebuild back to default dimensions with Netherite floor.
- `/dunefall addsand [rows]` – Adds more sand stratum without modifying or repairing the base floor & teleports to top.
- `/dunefall tp` – Emergency panic teleport to the highest sand block.
- `/dunefall stop` – Pause or resume the active round timer.
- `/dunefall timer [seconds]` – Adjust the countdown timer limit.
- `/dunefall edit` – Toggle arena build protection for live customization.
- `/dunefall wl [reset]` – View or reset your live-stream Win/Loss record.
- `/dunefall damage_protection` – Toggle fall, explosion, and mob damage protection.

### HUD & Display Control
- `/hud` *(or `/dunefall hud`)* – Toggle the entire HUD (Scoreboard, BossBar, Action Bar) on/off.
- `/hud hide` *(or `/hidehud`)* – Instantly hide all HUD overlays.
- `/hud show` *(or `/showhud`)* – Restore all HUD overlays.
- `/hud status` – Display diagnostic status of all individual UI subsystems.
- `/dunefall scoreboard` – Toggle the sidebar scoreboard independently.
- `/dunefall bossbar [remove/show/lower/top/actionbar]` – Customize BossBar positioning or toggle action bar progress.
- `/dunefall leaderboards` – Display the viewer interaction leaderboard in chat.

### Economy, Shop & Gear
- `/shop` *(or `/dunefall shop`)* – Open the interactive Specimen Shop GUI.
- `/sell` *(or `/dunefall sell [player]`)* – Liquidate all inventory blocks for coins.
- `/dunefall repair [player]` – Restore equipped armor, held tools, or weapons back to 100% durability (2 coins/durability).
- `/dunefall autorepair [on/off/status]` – Toggle or check real-time auto-repair status (2 coins/durability, activates below 50 durability until 100% recovered).
- `/dunefall upgrade [player]` – Overclock held equipment by +1 Level (up to Lv 120).
- `/dunefall coins [player]` – Check specimen coin balance.
- `/dunefall givecoins [player] [amount]` – Grant coins to a player.
- `/dunefall shovel` – Grant the master Obsidian Excavator shovel.
- `/dunefall speed [level]` – Adjust excavation mining haste level.

---

## ⚙️ Configuration Preview (`config.yml`)

```yaml
# ===================================================================
#  D U N E F A L L  -  Interactive Mini-Game & StreamTK Manager
# ===================================================================

# HUD & Display Settings
hud:
  enabled: true # Master switch for in-game HUD

# BossBar & Progress Bar Settings
bossbar:
  enabled: true
  lower: true # Shift progress bar below top edge to avoid TikTok UI clash
  action_bar_progress: true

# Sidebar Scoreboard Settings
scoreboard:
  enabled: true

# Game Timer & Win Condition
game:
  default_timer_seconds: 300
  low_time_warning_seconds: 30
  auto_start_timer: true
  auto_reset_on_end: true
  round_reset_delay_seconds: 5
  preserve_base_on_end: true # Preserve base platform on win/loss; adds sand and teleports to top

# Arena Defaults
arena:
  default_size: 7
  default_height: 12
  default_sand: "SAND"
  wall_material: "TINTED_GLASS"
  floor_default: "NETHERITE_BLOCK"
  instant_fall_physics: true
  drop_sand: false # Blocks vanish cleanly without entity clutter
```

---

## 🚀 Installation & Quick Start

1. Download **`DuneFall-1.0.0.jar`**.
2. Drop it into your server's `plugins/` folder (Paper 1.21+ recommended).
3. Start or reload the server.
4. Join the game and type:
   ```bash
   /dunefall create 7 12
   ```
5. Equip your shovel with `/shop` or `/dunefall shovel` and start your TikTok stream!

---

## 🛡 Permissions

- `dunefall.admin` *(Default: OP)* — Full administrative access to arena setup and controls.
- `dunefall.streamer` *(Default: OP)* — Streamer commands: `/shop`, `/sell`, `/hud`, `/dunefall tp`, `/dunefall repair`.
- `dunefall.viewer` *(Default: OP)* — Console trigger access for live gift interactions.

---

<p align="center">
  <b>Engineered with precision for high-traffic TikTok Live Streamers.</b><br>
  <i>PaperMC 1.21+ • GeyserMC Crossplay Ready • Zero Performance Overhead</i>
</p>
