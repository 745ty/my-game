# Roguelike Action Game Design Document (Python/Pygame)

## 1. Game Concept
- **Title**: *Soul Guardian* (Placeholder)
- **Genre**: 2D Top-down Shooter / Roguelike
- **Inspiration**: *Soul Knight*, *Enter the Gungeon*
- **Core Loop**: Enter Dungeon -> Fight Enemies -> Get Loot -> Next Level / Die & Restart

## 2. Core Mechanics
### Player
- **Movement**: WASD keys for 8-directional movement.
- **Aiming**: Mouse cursor position.
- **Shooting**: Left Mouse Button (LMB).
- **Stats**: HP, Energy (Mana), Armor (optional).

### Combat
- **Weapons**: Pistol (default), Shotgun, Laser, Melee.
- **Projectiles**: Bullets with travel time and collision detection.
- **Enemies**:
  - *Chaser*: Moves towards player, deals contact damage.
  - *Shooter*: Stays at range, shoots projectiles at player.

### Level Generation (Future)
- Randomly generated rooms connected by corridors.
- Wave-based spawning in rooms.

## 3. Technical Stack
- **Language**: Python 3.x
- **Library**: Pygame (Community Edition recommended `pygame-ce`)
- **Architecture**:
  - `Game` class: Manages states (Menu, Playing, GameOver).
  - `EntityManager`: Handles all sprites and collisions.
  - `Sprite` classes: Player, Enemy, Bullet.

## 4. Art Style
- Simple 2D geometric shapes for prototype (Player = Blue Circle, Enemy = Red Square).
- Pixel art assets can be added later.

## 5. MVP Goals (Phase 1)
1.  Player can move and shoot.
2.  Enemies spawn and chase player.
3.  Player can kill enemies; enemies can damage player.
4.  Game Over screen when HP hits 0.
