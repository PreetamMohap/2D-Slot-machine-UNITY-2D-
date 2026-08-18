# 🎰 Unity 2D Slot Machine Game

A fully interactive 2D Slot Machine game built in Unity (C#) adhering to Object-Oriented Programming (OOP) principles, clean modular architecture, customizable bet economy, smooth reel animations, and WebGL browser support.

---

## 📄 1. Game Overview

- **3-Reel Gameplay**: Classic 3-reel casino slot layout with custom graphical assets.
- **Fair RNG Outcomes**: Independent Random Number Generator selection per reel on every spin.
- **Dynamic Payout & Economy**: Customizable bet controls ($5 to $100 coins), total credit tracking, and payouts calculated dynamically based on symbol multipliers (100x, 50x, 25x, 10x).
- **Dead-Center Symbol Alignment**: Pixel-perfect layout locking (`Pos Y = -9`) ensuring symbols land dead-center in the window cutouts every spin.
- **Staggered Spin Animations**: Realistic physical downward rolling motion with staggered reel stopping (Reel 0 → Reel 1 → Reel 2).

---

## 🚀 2. Instructions to Run WebGL Build

### Option A: Local Server (Command Line)
1. Navigate to the `/Build/WebGL` folder in this repository.
2. Open terminal/command prompt and start a local HTTP server:
   ```bash
   python -m http.server 8000
   ```
3. Open your web browser and navigate to:
   👉 `http://localhost:8000`

### Option B: Local Server (VS Code / Unity)
1. Open the repository root in VS Code and launch `index.html` using the **Live Server** extension.
2. Alternatively, open the project in Unity and select **File → Build Settings → Build and Run**.

---

## 🌟 3. Bonus Features & Creative Additions

- **Interactive Arcade Lever**: Spin trigger bound to the 3D arcade side lever for authentic casino feel.
- **Dynamic Bet Adjuster**: Functional `+` (Increase Bet) and `-` (Decrease Bet) buttons dynamically calculating potential winning payouts.
- **5-Second Auto-Dismiss Jackpot Banner**: When 3 matching symbols align across the middle line, a **JACKPOT WIN** popup appears for 5 seconds, auto-closes, and unlocks the lever for continuous play.
- **Frame-Independent Layout Enforcer**: `LateUpdate()` position locking preventing UI layout drift across different aspect ratios.

---

## 🧠 4. Thought Process & Technical Approach

1. **Modular Object-Oriented Architecture**:
   - `SymbolData.cs` (`ScriptableObject`): Data container defining Symbol ID, Sprite, and Payout Multiplier.
   - `ReelController.cs`: Handles single reel physics, downward rolling animations, and target symbol alignment.
   - `SlotMachineManager.cs`: Game loop controller managing RNG outcome generation, bet deductions, win evaluation, and payout distribution.
   - `UIManager.cs`: Handles Canvas UI text updates, button state locking, and win banner popups.

2. **Data-Driven Symbol Extensibility**:
   - Symbols are managed via `ScriptableObject` assets, allowing new symbols, sprites, or payout multipliers to be added without modifying source code.

3. **Smooth Casino Game Feel**:
   - Implemented staggered reel stopping delays (Reel 0 stops → Reel 1 stops 0.4s later → Reel 2 stops 0.8s later) to build player anticipation during spins.
