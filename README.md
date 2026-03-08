# Shadow of the Demon King

> A LOTR-inspired 2D top-down horror game built with Python + Pygame

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pygame](https://img.shields.io/badge/Pygame-2.0+-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Status](https://img.shields.io/badge/Status-Prototype-orange.svg)

## 🎮 Overview

**Shadows of Mordor** is a top-down 2D horror action game where you play as **The Last Warden**, fighting through six cursed realms to defeat **Gorgoroth the Demon King**.

### Key Features

✅ **5 Atmospheric Levels + Final Boss Fight**  
✅ **LOTR-Inspired Dark Fantasy Horror**  
✅ **Top-Down Combat & Exploration**  
✅ **Enemy AI (Wander + Aggro)**  
✅ **Multi-Phase Boss Battle**  
✅ **Particle Effects & Visual Feedback**  
✅ **Smooth Camera System**  
✅ **Key/Exit Progression Mechanics**  

---

## 🕹️ Controls

| Action | Keys |
|--------|------|
| **Move** | WASD or Arrow Keys |
| **Attack** | SPACE |
| **Confirm/Start** | ENTER |

---

## 📦 Installation & Running

### Prerequisites
- Python 3.8 or higher
- Pygame 2.0+

### Install Dependencies
```bash
pip install pygame
```

### Run the Game
```bash
python main.py
```

---

## 🗺️ Level Structure

### Level 1: The Darkened Shire
🌑 **Theme:** Quiet horror, abandoned village  
👾 **Enemies:** Corrupted villagers  
🎯 **Objective:** Escape to the mines  

### Level 2: Mines of Moria
⛏️ **Theme:** Claustrophobic stone corridors  
👾 **Enemies:** Cave dwellers  
🎯 **Objective:** Navigate the ancient darkness  

### Level 3: The Dead Marshes
💀 **Theme:** Ghostly fog and treacherous terrain  
👾 **Enemies:** Wraiths and spirits  
⚠️ **New Hazard:** Spike traps  
🎯 **Objective:** Survive the dead  

### Level 4: Tower of Barad-dûr
🏰 **Theme:** Fortress of the Eye  
👾 **Enemies:** Elite guards (6+ enemies)  
🎯 **Objective:** Climb the tower  

### Level 5: Mount Doom - The Approach
🌋 **Theme:** Volcanic wasteland  
👾 **Enemies:** Mixed threats + traps  
🎯 **Objective:** Reach the final gate  

### Level 6: BOSS FIGHT - Gorgoroth the Demon King
👹 **Boss:** Gorgoroth (30 HP, 2 phases)  
⚔️ **Phase 1:** Slow pursuit, single fireballs  
🔥 **Phase 2:** Enraged, triple-shot, faster  
🎯 **Objective:** Defeat the Demon King  

---

## 🎨 Art Style

- **Programmer art aesthetic** with geometric shapes
- **Color-coded themes** (greens → grays → oranges → reds)
- **Particle effects** for combat feedback
- **Simple but effective** visual design

---

## 🛠️ Tech Stack

- **Engine:** Pygame (2D game library)
- **Language:** Python 3.8+
- **Architecture:** Object-oriented (Sprite classes)
- **Rendering:** 60 FPS target, tile-based maps
- **Collision:** Rect-based AABB
- **Camera:** Smooth following with bounds

---

## 📁 Project Structure

```
shadows-of-mordor/
├── main.py                    # Complete game (monolithic)
├── GAME_DESIGN_DOCUMENT.md    # Full GDD
├── README.md                  # This file
└── requirements.txt           # pygame>=2.0.0
```

---

## 🚀 Roadmap

### ✅ Phase 1: Core Prototype (COMPLETE)
- [x] Player movement & collision
- [x] Enemy AI (wander + aggro)
- [x] Combat system
- [x] 5 levels + boss fight
- [x] Progression (keys, exits)
- [x] HUD & UI screens

### 🔄 Phase 2: Polish (Current)
- [ ] Sound effects (pygame.mixer)
- [ ] Sprite animations (walk cycles)
- [ ] Screen shake on hits
- [ ] More particle variety

### 📦 Phase 3: Expansion
- [ ] Additional levels (10+ total)
- [ ] Mid-bosses
- [ ] Difficulty modes
- [ ] Achievements

### 🚀 Phase 4: Distribution
- [ ] PyInstaller packaging (.exe)
- [ ] itch.io release
- [ ] Trailer & marketing

---

## 🎮 Gameplay Tips

1. **Master dodge timing** — invincibility frames after getting hit
2. **Kite enemies** — let them chase, attack during cooldowns
3. **Watch boss patterns** — learn fireball timing
4. **Collect health pickups** — don't rush, explore carefully
5. **Clear all enemies** — required before exit unlocks

---

## 🐛 Known Issues

- No sound effects yet (visual-only)
- Static sprites (no animations)
- Boss fireballs can clip through walls (intentional difficulty?)

---

## 🤝 Contributing

This is a solo dev project, but feedback and suggestions are welcome!

**How to help:**
1. Playtest and report bugs (GitHub Issues)
2. Suggest features (Discussions)
3. Create fan art or level designs
4. Share the game with others

---

## 📜 License

MIT License — free to use, modify, and distribute.

---

## 🙏 Credits

**Developer:** Solo indie project  
**Engine:** Pygame (pygame.org)  
**Inspiration:** Lord of the Rings (J.R.R. Tolkien)  
**Art Style:** Programmer art (original)  

---

## 📚 Resources

- **[Full Game Design Document](GAME_DESIGN_DOCUMENT.md)** — Complete technical specs
- **[Pygame Docs](https://www.pygame.org/docs/)** — Official documentation
- **[r/pygame](https://reddit.com/r/pygame)** — Community support

---

## 🎯 Why Pygame?

**Pygame is perfect for this project because:**
- ✅ Python-based (easy to learn, fast to prototype)
- ✅ 2D-focused (horror doesn't need 3D)
- ✅ Full control (no engine black boxes)
- ✅ Free and open-source
- ✅ Cross-platform (Windows, Mac, Linux)

**Comparison:**

| | Pygame | Unity | Godot |
|---|---|---|---|
| **Learning Curve** | Low | Medium | Medium |
| **2D Support** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Visual Editor** | ❌ | ✅ | ✅ |
| **Code Control** | ✅ Full | ⚠️ Partial | ✅ Full |
| **Best For** | 2D indie | All types | 2D/3D indie |

---

## 📸 Screenshots

*Coming soon — gameplay footage and boss fight clips*

---

## 🎵 Future Additions

### Sound Effects (Planned)
- Sword swings and impacts
- Enemy growls and deaths
- Boss roars and fireballs
- Ambient wind and echoes

### Music (Planned)
- Ominous title theme
- Ambient level tracks
- Intense boss battle music
- Victory fanfare

### Visual Upgrades (Planned)
- Animated walk cycles
- Attack animations
- Screen shake effects
- Lighting/fog effects

---

## 🔥 Quick Start (5 Minutes)

```bash
# 1. Clone or download the repo
git clone https://github.com/Beeloha/demon-king-horror-game.git
cd demon-king-horror-game

# 2. Install Pygame
pip install pygame

# 3. Run the game
python main.py

# 4. Play!
# WASD to move, SPACE to attack, defeat Gorgoroth!
```

---

**Carry the Flame. Face the Darkness. Defeat the Demon King.**

*Built with ❤️ and Python*