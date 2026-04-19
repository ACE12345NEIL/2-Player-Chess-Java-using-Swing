# ♟️ Chess Game

A fully-featured, two-player chess game built with **Java Swing**, wrapped in an elegant **ancient-themed** dark wood UI with gold accents. Play classic chess on a beautiful graphical interface complete with animated piece movement, a configurable chess clock, legal move highlighting, check detection, checkmate/stalemate resolution, pawn promotion, castling, en passant, and more.

---

## ✨ Features

| Feature | Description |
|---|---|
| **Ancient-Themed UI** | Dark wood background with gold accents, serif fonts, and ornate styled panels |
| **Chess Clock / Timer** | Selectable time controls: ∞ (no limit), 1 min, 3 min, 5 min, or 10 min per player |
| **Turn Indicator** | Prominent sidebar display showing whose turn it is, with distinct styling for White and Black |
| **Graphical Board** | 8×8 board with warm parchment & walnut squares, gold-labeled rows (1–8) and columns (A–H) |
| **Unicode Pieces** | Beautiful Unicode chess symbols — no image assets required |
| **Legal Move Highlighting** | Click a piece to see valid moves highlighted in gold; selected piece highlighted in sage green |
| **Smooth Animations** | Pieces glide from source to destination with an arc animation |
| **Castling** | King-side and queen-side castling fully implemented |
| **En Passant** | Special pawn capture rule correctly enforced |
| **Pawn Promotion** | Themed dialog lets you choose Queen, Rook, Bishop, or Knight on promotion |
| **Check Detection** | King under threat is highlighted in crimson |
| **Checkmate & Stalemate** | Game-ending conditions detected and announced with a styled dialog |
| **Move History** | Scrollable sidebar with algebraic-style notation (e.g. ♙ E2 → E4) |
| **Captured Pieces** | Separate panels display captured white and black pieces |
| **Reset / New Game** | Reset with same time control, or start a new game with a different one |

---

## 🏗️ Architecture

The project follows a clean **object-oriented** design with separation of concerns between game logic and presentation.

```
ChessGame/
├── src/
│   └── chess/
│       ├── Main.java                # Application entry point
│       ├── ChessGUI.java            # Swing GUI — board rendering, click handling, animations
│       ├── ChessGame.java           # Core game logic — turns, check, checkmate, special moves
│       ├── Board.java               # Board state — 8×8 grid of pieces
│       ├── Piece.java               # Abstract base class for all chess pieces
│       ├── Move.java                # Data class representing a move (start → end)
│       ├── InvalidMoveException.java# Custom exception for illegal moves
│       ├── Tile.java                # Tile representation
│       ├── Pawn.java                # ♙ Pawn — includes double-step, en passant tracking
│       ├── Rook.java                # ♖ Rook — horizontal/vertical sliding
│       ├── Knight.java              # ♘ Knight — L-shaped jumps
│       ├── Bishop.java              # ♗ Bishop — diagonal sliding
│       ├── Queen.java               # ♕ Queen — combined rook + bishop movement
│       └── King.java                # ♔ King — single-step + castling logic
├── out/                             # Compiled .class files (generated)
├── INSTALLATION.md                  # Installation & run guide
└── README.md                        # This file
```

### Class Diagram (Simplified)

```
                  ┌──────────┐
                  │   Main   │
                  └────┬─────┘
                       │ creates
                  ┌────▼─────┐
                  │ ChessGUI │ ◄── Swing UI, event handling, animation
                  └────┬─────┘
                       │ manages
                  ┌────▼──────┐
                  │ ChessGame │ ◄── Turn management, move validation, special rules
                  └────┬──────┘
                       │ operates on
                  ┌────▼─────┐
                  │  Board   │ ◄── 8×8 Piece[][] grid
                  └────┬─────┘
                       │ contains
                  ┌────▼─────┐
                  │  Piece   │ (abstract)
                  └────┬─────┘
        ┌───────┬──────┼──────┬────────┬────────┐
        │       │      │      │        │        │
      Pawn    Rook  Knight  Bishop   Queen    King
```

---

## 🚀 Quick Start

> **Prerequisites:** Java Development Kit (JDK) 11 or higher

```bash
# Clone the repository
git clone https://github.com/<your-username>/2-Player-Chess-Java--Swing-.git
cd 2-Player-Chess-Java--Swing-

# Compile
javac -encoding UTF-8 -d out src/chess/*.java

# Run
java -cp out chess.Main
```

For detailed setup instructions, see the **[Installation Guide](INSTALLATION.md)**.

---

## 🎮 How to Play

1. **Launch** the application — a **time control dialog** appears first.
2. **Select a time control:** ∞ (no limit), 1 min, 3 min, 5 min, or 10 min.
3. The board opens maximized. The **sidebar** shows whose turn it is and (if timed) each player's remaining clock.
4. **Click a piece** to select it. The selected piece turns **green** and all legal destination squares turn **gold**.
5. **Click a highlighted square** to move the piece. The piece animates to its new position.
6. **Turns alternate** between White and Black after each valid move.
7. **Check:** If a king is in check, its square turns **crimson red**.
8. **Promotion:** When a pawn reaches the opposite end, a themed dialog appears to choose a promotion piece.
9. **Castling:** Move the king two squares toward a rook to castle (if legal).
10. **Timer:** If a player's clock runs out, they lose. The timer turns red at ≤10 seconds.
11. **Game Over:** Checkmate, stalemate, or time-out is announced via a styled dialog.
12. **Reset:** Click **"↺ Reset"** to restart with the same time control, or **"♔ New Game"** to pick a new one.

---

## 🛠️ Development

### Requirements

| Tool | Version |
|---|---|
| JDK | 11+ (tested on 17 & 21) |
| OS | Windows, macOS, or Linux |
| IDE (optional) | VS Code, IntelliJ IDEA, Eclipse |

### Building from Source

```bash
# Compile all source files with UTF-8 encoding (required for Unicode piece symbols)
javac -encoding UTF-8 -d out src/chess/*.java
```

The `-encoding UTF-8` flag is **required** because the source files contain Unicode chess piece characters (♔ ♕ ♖ etc.).

### Running

```bash
# Via the Main entry point
java -cp out chess.Main

# Alternative: directly via ChessGUI (also has a main method)
java -cp out chess.ChessGUI
```

---

## 🗺️ Roadmap

- [ ] Undo / Redo move functionality
- [ ] AI opponent (single-player mode)
- [ ] Sound effects for moves and captures
- [ ] Highlight the last move played
- [ ] Dynamic window resizing for board and pieces
- [ ] PGN export / import for game records
- [ ] Additional themes (marble, modern minimalist)

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/my-feature`
3. **Commit** your changes: `git commit -m "Add my feature"`
4. **Push** to the branch: `git push origin feature/my-feature`
5. **Open** a Pull Request

Please make sure your code compiles cleanly with `javac -encoding UTF-8 -d out src/chess/*.java` before submitting.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  Made with ♟️ and Java
</p>
