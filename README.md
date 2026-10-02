# 🎮 Tic Tac Toe Game

A simple and interactive **Tic Tac Toe game** built using **HTML, CSS, and JavaScript**.

This project is a browser-based two-player game where players take turns placing **O** and **X** on a 3×3 game board. The application automatically checks for winning combinations, detects draws, displays the winner, and provides options to reset or start a new game.

---

## 📌 Project Overview

**Tic Tac Toe** is a classic two-player strategy game played on a 3×3 grid.

The objective is simple:

* Player O and Player X take turns.
* Each player selects an empty box.
* The first player to get three matching symbols in a row wins.
* A winning row can be:

  * Horizontal
  * Vertical
  * Diagonal
* If all nine boxes are filled without a winner, the game ends in a draw.

The game board consists of nine buttons, each representing one position in the 3×3 grid.

---

## ✨ Features

### 🎯 Two-Player Gameplay

The game supports two players:

```text
Player O
Player X
```

The game initially starts with **O's turn**, and the turn automatically switches between O and X after every valid move.

### 🏆 Automatic Winner Detection

The application checks the board after every move to determine whether one of the players has achieved a winning combination.

The game contains all **8 possible winning patterns**:

```text
[0, 1, 2]    → Top row
[3, 4, 5]    → Middle row
[6, 7, 8]    → Bottom row

[0, 3, 6]    → Left column
[1, 4, 7]    → Middle column
[2, 5, 8]    → Right column

[0, 4, 8]    → Main diagonal
[2, 4, 6]    → Other diagonal
```

These patterns are defined in the JavaScript game logic.

### 🤝 Draw Detection

If all nine boxes are filled and no player has won, the game displays:

```text
Game was a Draw.
```

The application keeps track of the number of moves using a `count` variable and checks whether all nine positions have been played.

### 🔄 Reset Game

The **Reset Game** button allows players to clear the board and start again.

The game resets:

* Player turn
* Move count
* All boxes
* Winner message

The project also provides a **New Game** button after a game ends.

### 🚫 Disable Used Boxes

Once a player selects a box, that box is disabled so it cannot be selected again.

### 📢 Winner Message

When a player wins, the application displays a congratulatory message containing the winning player's symbol:

```text
congratulation, winner is O
```

or

```text
congratulation, winner is X
```

---

## 🛠️ Technologies Used

| Technology     | Purpose                                                              |
| -------------- | -------------------------------------------------------------------- |
| **HTML5**      | Creates the game structure and 3×3 board                             |
| **CSS3**       | Handles layout, colors, buttons, sizing and styling                  |
| **JavaScript** | Controls game logic, turns, winner detection and reset functionality |

---

## 📂 Project Structure

```text
Tic-Tac-Toe/
│
├── index.html
├── style.css
├── script.js
└── README.md
```

---

## 🧱 HTML Structure

The HTML file contains:

* Game title
* 3×3 game board
* Nine game buttons
* Winner/draw message container
* New Game button
* Reset Game button

The game board is created using nine buttons with the `.box` class.

Example:

```html
<div class="game">
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
    <button class="box"></button>
</div>
```

---

## 🎨 CSS Design

The game uses a centered layout with a colored background and responsive sizing.

The main game board uses:

```css
.game {
    height: 60vmin;
    width: 60vmin;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 1.5vmin;
}
```

This allows the nine boxes to form a responsive 3×3 grid.

Each box is styled with:

* Rounded corners
* Shadow
* Large text
* Light background
* Responsive dimensions

---

## ⚙️ JavaScript Game Logic

### 1. Selecting Game Elements

JavaScript first selects the required HTML elements:

```javascript
let boxes = document.querySelectorAll(".box");
let resetbtn = document.querySelector("#reset-btn");
let newGameBtn = document.querySelector("#new-btn");
let msgContainer = document.querySelector(".msg-container");
let msg = document.querySelector("#msg");
```

These elements are then used to control the game.

---

### 2. Managing Player Turns

The game uses:

```javascript
let turnO = true;
```

When `turnO` is `true`, the current player places **O**.

Otherwise, the player places **X**.

After each move, the turn changes:

```javascript
if (turnO) {
    box.innerText = "O";
    turnO = false;
} else {
    box.innerText = "X";
    turnO = true;
}
```

---

### 3. Tracking Moves

The project uses:

```javascript
let count = 0;
```

Every time a player makes a move:

```javascript
count++;
```

This allows the application to determine when all nine boxes have been filled.

---

### 4. Checking for a Winner

After every move:

```javascript
let isWinner = checkWinner();
```

The `checkWinner()` function loops through every winning pattern and compares the values of the three corresponding boxes.

If all three positions contain the same symbol:

```javascript
if (pos1val == pos2val && pos2val == pos3val) {
    showWinner(pos1val);
    return true;
}
```

The winner is then displayed.

---

## 🏆 Winning Conditions

There are eight possible winning combinations:

### Horizontal

```text
O | O | O
---------
  |   |
---------
  |   |
```

### Vertical

```text
O |   |
---------
O |   |
---------
O |   |
```

### Diagonal

```text
O |   |
---------
  | O |
---------
  |   | O
```

The JavaScript represents these positions using array indexes.

---

## 🤝 Draw Logic

After checking for a winner, the game checks:

```javascript
if (count === 9 && !isWinner) {
    gameDraw();
}
```

If all nine moves have been completed without a winner, the game displays the draw message and disables the board.

---

## 🔄 Reset Functionality

The `resetGame()` function restores the initial state:

```javascript
const resetGame = () => {
    turnO = true;
    count = 0;
    enableBoxes();
    msgContainer.classList.add("hide");
}
```

This resets the player to O, clears the move count, enables all boxes, and hides the result message.

---

## ▶️ How to Run the Project

### Method 1: Open Directly

1. Download or clone the repository.
2. Open the project folder.
3. Open `index.html` in a web browser.

### Method 2: Using VS Code

1. Open the project in **Visual Studio Code**.
2. Install the **Live Server** extension.
3. Right-click `index.html`.
4. Select **Open with Live Server**.
5. The game will open in your browser.

---

## 🎮 How to Play

1. The game starts with **Player O**.
2. Click any empty box.
3. Player X takes the next turn.
4. Continue alternating between O and X.
5. Try to get three matching symbols in:

   * A row
   * A column
   * A diagonal
6. The first player to achieve this wins.
7. If all nine boxes are filled without a winner, the game is a draw.
8. Click **Reset Game** or **New Game** to play again.

---

## 🧠 Concepts Practiced

This project helped practice several important JavaScript and frontend concepts:

* DOM Manipulation
* `querySelector()` and `querySelectorAll()`
* Event Listeners
* JavaScript Functions
* Conditional Statements
* Arrays
* Loops
* Boolean Variables
* Template Literals
* Button states
* Game-state management
* CSS Flexbox
* Responsive units such as `vmin`
* Basic algorithmic logic

---

## 🔮 Future Improvements

Some features that could be added in future versions:

* 🤖 **Play against Computer**
* 🧠 Different AI difficulty levels
* 🏆 Scoreboard for multiple rounds
* 👥 Player name input
* 🎨 Multiple themes
* 🔊 Sound effects
* ✨ Winning animation
* 📱 Improved mobile UI
* 🌐 Online multiplayer
* 🌓 Dark/Light mode
* 📊 Match history
* 🏅 Player statistics

---

## 🎯 Project Objective

The main objective of this project was to create a simple interactive browser game while strengthening fundamental **HTML, CSS, and JavaScript** skills.

The project demonstrates how JavaScript can be used to manage game state, handle user interactions, evaluate winning conditions, and dynamically update the webpage.

---

## 📸 Project Preview

Add a screenshot of your game here:

```markdown
![Tic Tac Toe Game](screenshot.png)
```

---

## 👨‍💻 Author

**Rishu Kumar Rana**

B.Tech Computer Science & Engineering Graduate

### Interests

* Web Development
* JavaScript
* Python
* Data Analytics
* Data Science

---

## ⭐ Support

If you found this project useful or interesting, consider giving the repository a ⭐ on GitHub.

---

## 📄 License

This project was created for **learning and educational purposes**.
