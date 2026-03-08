# Shadow of the Demon King
## Game Design Document (2D Pygame Edition)

---

## 1. Executive Summary

**Title:** Shadow of the Demon King (Shadows of Mordor)  
**Genre:** 2D Top-Down Horror / Survival / Action  
**Platform:** PC (Windows, Mac, Linux via Pygame)  
**Target Audience:** 16+ (fans of horror, dark fantasy, and LOTR aesthetics)  
**Engine:** Python + Pygame  
**Core Concept:** A 2D top-down horror game inspired by Lord of the Rings atmosphere. Navigate cursed lands, defeat nightmarish creatures, collect keys, and confront Gorgoroth the Demon King in an epic final boss battle.

---

## 2. Story & Lore

### Setting
The world was once a thriving kingdom blessed by ancient magic. When the Demon King Gorgoroth awoke from his prison beneath the mountains, darkness swept across the land. The Shire fell silent, forests twisted into nightmares, and the dead began to walk.

You are **The Last Warden** — a lone survivor tasked with carrying hope through six corrupted realms to reach Gorgoroth's throne and end his reign of terror.

### Themes
- **Hope vs. Despair:** You are the last light in a dying world
- **Corruption:** The land itself rejects life
- **Ancient Evil:** Gorgoroth is a primordial force, not just a villain
- **Isolation:** You face the darkness alone

### Inspirations from LOTR
- The oppressive atmosphere of Mordor
- The ancient evil and corruption of Sauron
- Gothic architecture of Minas Morgul and Barad-dûr
- Nazgûl-inspired wraith enemies
- The Dead Marshes and Mount Doom

---

## 3. Core Gameplay Mechanics

### Perspective & Controls
- **Top-down 2D view** with camera following the player
- **WASD / Arrow Keys:** Movement (8-directional)
- **SPACE:** Melee attack in facing direction
- **Smooth pixel movement** with wall collision

### Combat System
- **Melee combat:** Close-range attacks with directional swings
- **Attack cooldown:** Prevents spam, requires timing
- **Enemy AI:**
  - Wander behavior when idle
  - Aggro within detection radius (~200px)
  - Pathfinding around walls
  - Attack cooldowns to allow counter-play
- **Damage feedback:** Flash effects, particle systems, health bars
- **Invincibility frames:** Brief immunity after taking damage

### Progression
- **Health system:** 5 hearts, can be restored with health pickups
- **Key collection:** Required to unlock exits
- **Clear conditions:** Defeat all enemies + collect key to progress
- **Level-based structure:** 5 levels + final boss fight

### Hazards
- **Spike traps:** Static environmental damage with cooldowns
- **Enemy variety:** Different behaviors per level
- **Boss mechanics:** Multi-phase fight with projectiles and enhanced aggression

---

## 4. Level Design

### Level 1: The Darkened Shire
**Atmosphere:** Quiet horror, abandoned homes, creeping shadows  
**Visual Theme:** Dark greens, dying grass  
**Enemies:** Basic corrupted villagers (3 HP, slow aggro)  
**Mechanics Introduction:**
- Movement and collision
- Basic combat
- Key collection
- Exit requirement

**Objective:** Escape the Shire and reach the cursed mines

---

### Level 2: Mines of Moria
**Atmosphere:** Claustrophobic stone corridors, ancient darkness  
**Visual Theme:** Gray stone, dark shadows  
**Enemies:** Cave dwellers with tighter patrol patterns  
**New Mechanics:**
- Tighter corridors (navigation challenge)
- Multiple enemy encounters

**Objective:** Delve through the mines to reach the marshes

---

### Level 3: The Dead Marshes
**Atmosphere:** Ghostly faces, fog, treacherous terrain  
**Visual Theme:** Murky greens, brown muck  
**Enemies:** Wraiths and corrupted spirits  
**New Mechanics:**
- **Spike traps** introduced
- More complex maze layout
- Health pickups scattered

**Objective:** Navigate the marshes without falling to the dead

---

### Level 4: Tower of Barad-dûr
**Atmosphere:** The Eye watches all, oppressive architecture  
**Visual Theme:** Dark oranges, burnt reds, stone fortress  
**Enemies:** Elite guards, higher HP and damage  
**Mechanics:**
- Dense enemy encounters (6+ enemies)
- Narrow fortress corridors
- Strategic combat required

**Objective:** Climb the tower to reach the mountain approach

---

### Level 5: Mount Doom - The Approach
**Atmosphere:** Fire, ash, volcanic wasteland  
**Visual Theme:** Oranges, blacks, volcanic rock  
**Enemies:** Mixed enemy types + spike traps  
**New Mechanics:**
- Combined hazards (enemies + traps)
- Final preparation before boss

**Objective:** Cross the wasteland to face Gorgoroth

---

### Level 6: BOSS FIGHT - Gorgoroth the Demon King

**Appearance:**
- 64x64 sprite (double player size)
- Demon horns, glowing eyes (orange/yellow)
- Dark red/black color scheme
- Pulsing aura effect

**Phase 1: The Dark Lord (30 HP → 15 HP)**
- **Movement:** Slow pursuit (0.8 speed)
- **Melee Attack:** 2 damage, 75 tick cooldown
- **Projectile Attack:** Single fireball every 240 ticks
- **Particle Effects:** Orange flame particles
- **Strategy:** Learn attack patterns, dodge fireballs, strike during cooldowns

**Phase 2: Enraged (15 HP → 0 HP)**
- **Trigger:** Roar effect at 50% HP
- **Enhanced Stats:**
  - Speed increased to 1.4
  - Damage increased to 3
  - Melee cooldown reduced to 75 ticks
- **Triple Shot:** Fires 3 fireballs in spread pattern every 150 ticks
- **Increased Aggression:** Faster, more relentless pursuit
- **Visual Changes:** Red aura, more particles

**Victory Condition:** Reduce Gorgoroth to 0 HP without dying

---

## 5. Technical Implementation (Pygame)

### Architecture

**Core Systems:**
- `Player` class: Movement, combat, health, particle effects
- `Enemy` class: AI (wander/aggro), collision, health bars
- `Boss` class: Multi-phase logic, projectiles, particle effects
- `Camera` class: Smooth following with map bounds
- `Particle` system: Visual feedback for hits, attacks, effects
- Sprite groups for collision detection and rendering

**Map System:**
- **ASCII tile maps** stored in level dictionaries
- **Tile-based collision** (48x48 pixel tiles)
- **Dynamic entity spawning** from map data:
  - `#` = Wall
  - `.` = Floor
  - `P` = Player spawn
  - `E` = Enemy spawn
  - `B` = Boss spawn
  - `K` = Key
  - `X` = Exit
  - `T` = Spike trap
  - `H` = Health pickup

**Rendering Pipeline:**
1. Clear screen
2. Draw floors (background layer)
3. Draw walls
4. Draw traps, items, exits
5. Draw enemies (with health bars)
6. Draw boss (with aura, projectiles, particles)
7. Draw player (with particles, attack indicator)
8. Draw HUD overlay
9. Flip display

**Game Loop:**
- **60 FPS** target
- Event handling → Input → Update → Collision → Render
- State machine: Title → Story → Level → (Victory/Game Over) → Loop

---

## 6. Art Style & Visuals

### Visual Direction
- **Programmer art aesthetic** with clean shapes and bold colors
- Simple geometric sprites (circles, rectangles, polygons)
- **Color-coded themes** per level:
  - Shire: Dark greens
  - Moria: Grays
  - Marshes: Murky greens/browns
  - Barad-dûr: Oranges/reds
  - Mount Doom: Volcanic oranges/blacks
- **Particle effects** for visual feedback (blood, fire, magic)
- **UI polish:** Health hearts, boss health bar, message flashes

### Sprite Design

**Player (32x32):**
- Tan/brown hooded figure
- Simple humanoid shape
- Black eyes

**Enemy (32x32):**
- Green/dark corrupted body
- Red glowing eyes
- White claws/teeth

**Boss (64x64):**
- Demon horns
- Dark red armored body
- Glowing orange/yellow eyes
- Wing shapes
- Pulsing aura

**Items:**
- **Key:** Yellow circular outline + stem
- **Health:** Red cross
- **Exit:** Blue portal with "EXIT" text

**Traps:**
- **Spikes:** Gray triangular spikes emerging from floor

---

## 7. Audio & Atmosphere

### Music (Future Implementation)
- **Ambient horror soundscapes** for exploration
- **Intense orchestral scores** for boss fight
- **Silence** used strategically for tension

### Sound Design (Future Implementation)
- Attack swings and impacts
- Enemy hurt/death sounds
- Key pickup chime
- Boss roar and fireball sounds
- Ambient wind, dripping water, echoes

### Current State
- **Visual-only** implementation
- Sound effects can be added via `pygame.mixer`
- Recommended: Freesound.org for free SFX

---

## 8. Game Flow

### Screen Sequence

1. **Title Screen**
   - Animated title with pulsing effect
   - Controls display
   - "Press ENTER to begin"

2. **Story Screen** (per level)
   - Level name
   - Story text
   - "Press any key to continue"

3. **Level Gameplay**
   - HUD: Health hearts, level name, enemy count, key indicator
   - Flash messages for pickups and locked exits
   - Real-time combat and exploration

4. **Boss Intro Screen** (Level 6 trigger)
   - "GORGOROTH AWAKENS"
   - Dramatic presentation

5. **Victory/Defeat Screens**
   - **Level Clear:** Green celebration, advance to next level
   - **Game Over:** Red blood screen, return to title
   - **Victory:** Golden particles, final celebration

---

## 9. Development Roadmap

### ✅ Phase 1: Core Prototype (COMPLETE)
- [x] Player movement and collision
- [x] Enemy AI (wander + aggro)
- [x] Combat system
- [x] 5 levels + boss fight
- [x] Key/exit progression
- [x] Health system
- [x] Camera system
- [x] Particle effects
- [x] HUD and UI screens

### 🔄 Phase 2: Polish & Enhancement (Current)
- [ ] **Sound effects** (pygame.mixer)
  - Attack sounds
  - Hurt/death sounds
  - Ambient background tracks
- [ ] **Visual upgrades**
  - Animated sprites (walk cycles)
  - Screen shake on hits
  - Better particle variety
- [ ] **Additional mechanics**
  - Ranged weapon pickup
  - Stamina/dodge roll
  - Enemy variety (archers, tanks)

### 📦 Phase 3: Content Expansion
- [ ] **More levels** (extend to 10+ levels)
- [ ] **Additional bosses** (mid-bosses per 2-3 levels)
- [ ] **Difficulty modes** (Easy/Normal/Hard)
- [ ] **Achievements/unlockables**

### 🚀 Phase 4: Distribution
- [ ] **PyInstaller packaging** (standalone .exe)
- [ ] **itch.io upload** for distribution
- [ ] **Trailer creation** (screen recording + editing)
- [ ] **Community feedback** and iteration

---

## 10. Code Structure

### File Organization

```
shadows-of-mordor/
├── main.py                 # Current monolithic implementation
├── assets/                 # Future: sprites, sounds, music
│   ├── sprites/
│   ├── sounds/
│   └── music/
├── levels/                 # Future: external level data (JSON/CSV)
├── README.md
└── requirements.txt        # pygame>=2.0.0
```

### Recommended Refactoring (Future)

**Modular Structure:**
```
game/
├── __init__.py
├── main.py              # Game loop and state machine
├── entities.py          # Player, Enemy, Boss classes
├── components.py        # Particle, Camera, etc.
├── levels.py            # Level data and loading
├── screens.py           # Title, Story, Victory, etc.
├── utils.py             # Helper functions
└── config.py            # Constants (WIDTH, HEIGHT, COLORS, etc.)
```

**Benefits:**
- Easier to maintain
- Cleaner imports
- Collaborative development
- Unit testing support

---

## 11. Pygame-Specific Considerations

### Performance
- **Target:** 60 FPS on modern hardware
- **Optimization tips:**
  - Use sprite groups efficiently
  - Minimize per-frame allocations
  - Dirty rect rendering for large maps (future)
  - Limit particle count (current: reasonable)

### Cross-Platform
- **Pygame runs on:** Windows, Mac, Linux
- **Python version:** 3.8+ recommended
- **Distribution:**
  - PyInstaller for standalone executables
  - Source distribution via GitHub

### Limitations
- **2D only** (no 3D without OpenGL extensions)
- **No built-in animation system** (manual frame management)
- **Manual sprite creation** (no visual editor)

### Advantages
- **Rapid prototyping** (Python's ease of use)
- **Full control** (no engine black boxes)
- **Lightweight** (small file size)
- **Free and open-source**

---

## 12. Asset Creation Guidelines

### Sprite Art (Future Upgrades)

**Tools:**
- **Aseprite** (pixel art, $20 or compile free)
- **Piskel** (free browser-based pixel editor)
- **GIMP** (free, general-purpose)

**Sprite Specs:**
- **Player:** 32x32 pixels
- **Enemies:** 32x32 pixels
- **Boss:** 64x64 pixels
- **Tiles:** 48x48 pixels
- **Items:** 20-24 pixels

**Animation Frames:**
- Walk cycle: 4-8 frames
- Attack: 3-5 frames
- Idle: 2-4 frames (optional breathing)

### Sound Effects

**Sources:**
- **Freesound.org** (Creative Commons)
- **OpenGameArt.org**
- **Create your own** (Audacity, Bfxr)

**Needed Sounds:**
- Sword swing (whoosh)
- Hit impact (thud)
- Enemy death (growl/fade)
- Key pickup (chime)
- Fireball launch/impact
- Boss roar
- Footsteps (optional)

### Music

**Tools:**
- **LMMS** (free DAW)
- **Bosca Ceoil** (simple, free)
- **Beepbox** (browser-based)

**Tracks Needed:**
- Title theme (ominous, slow)
- Level ambience (1-2 variants)
- Boss fight (intense, fast)
- Victory fanfare (triumphant)

---

## 13. Playtesting Focus Areas

### Balance
- [ ] Player health: Is 5 HP fair?
- [ ] Enemy damage: Too punishing?
- [ ] Boss difficulty: Achievable but challenging?
- [ ] Level length: 2-5 minutes per level?

### Feel
- [ ] Movement speed: Responsive?
- [ ] Attack timing: Satisfying?
- [ ] Enemy AI: Fair but threatening?
- [ ] Camera: Smooth and helpful?

### Progression
- [ ] Difficulty curve: Gradual increase?
- [ ] Level variety: Distinct themes?
- [ ] Pacing: Action vs. exploration balance?

---

## 14. Monetization & Distribution

### Pricing Strategy
- **Free (itch.io):** Build audience, gather feedback
- **Pay-what-you-want:** Optional support
- **Premium ($3-5):** After polish and content expansion

### Platforms
- **itch.io:** Primary indie platform
- **GitHub:** Open-source community version
- **Steam:** Possible after significant polish (Steamworks integration required)

### Marketing
- **Gameplay GIFs** (share on Twitter/Reddit)
- **Devlog series** (itch.io blog, YouTube)
- **Playable web demo** (Pygbag for browser export)
- **Community engagement** (r/pygame, r/indiegames)

---

## 15. Success Metrics

### Phase 1 (Prototype)
- ✅ Complete 5-level game loop
- ✅ Boss fight implementation
- ✅ Core mechanics functional

### Phase 2 (Polish)
- [ ] Sound effects integrated
- [ ] 10+ playtest sessions
- [ ] 90%+ positive feedback

### Phase 3 (Release)
- [ ] 1,000+ downloads (itch.io)
- [ ] 50+ ratings (4+ stars average)
- [ ] Active community (Discord, subreddit)

---

## 16. Key Challenges & Solutions

### Challenge: Pygame is 2D-only
**Solution:** Lean into top-down horror (Darkwood, Hotline Miami aesthetic). Focus on atmosphere through color, particles, and level design.

### Challenge: No built-in animation system
**Solution:** Start with static sprites (current). Add sprite sheets and frame cycling in Phase 2.

### Challenge: Limited asset creation skills
**Solution:** Use programmer art (current). Gradually upgrade with Aseprite or commission artists on Fiverr/itch.io.

### Challenge: Performance with many particles
**Solution:** Cap particle count per entity, use object pooling, profile with cProfile.

### Challenge: Distribution complexity
**Solution:** PyInstaller for desktop, Pygbag for web. Provide source on GitHub for transparency.

---

## 17. Comparison: Pygame vs. Other Engines

| Feature | Pygame | Unity | Godot |
|---------|--------|-------|-------|
| **Cost** | Free | Free (with splash) | Free |
| **Language** | Python | C# | GDScript/C# |
| **Learning Curve** | Low | Medium | Medium |
| **2D Support** | Excellent | Good | Excellent |
| **3D Support** | Minimal | Excellent | Good |
| **Visual Editor** | No | Yes | Yes |
| **Performance** | Good (2D) | Excellent | Excellent |
| **Distribution** | PyInstaller | Built-in | Built-in |
| **Asset Store** | Limited | Huge | Growing |
| **Best For** | Prototypes, 2D indie | All game types | 2D indie, 3D indie |

**Why Pygame for This Project:**
- Python's ease of learning
- Full code control (no engine black boxes)
- Fast iteration (no compile times)
- Perfect for solo dev horror indie game

---

## 18. Next Steps (Immediate)

1. **Playtest current build** (5-10 people)
2. **Add sound effects** (prioritize combat sounds)
3. **Sprite animation** (walk cycles for player/enemies)
4. **Level variety** (add 2-3 more levels)
5. **Boss fight polish** (screen shake, more particle effects)
6. **PyInstaller packaging** (create .exe for easy sharing)
7. **itch.io upload** (free download, gather feedback)

---

## Conclusion

**Shadow of the Demon King** (Shadows of Mordor) demonstrates that Pygame is a viable, powerful tool for creating atmospheric 2D horror games. The top-down perspective allows for strategic combat, environmental storytelling, and LOTR-inspired dread without requiring 3D assets or complex engine knowledge.

The current prototype is **feature-complete** and playable. With sound, animation, and content expansion, this game can become a compelling indie horror experience that honors the dark fantasy legacy of Lord of the Rings while standing as a unique Pygame achievement.

**The journey from the Darkened Shire to Gorgoroth's throne is complete. Now, polish the path and share it with the world.**

---

*Carry the code. Face the bugs. Defeat the Demon King.*