# Крестики-нолики с валютой и выбором сложности

Игра «Крестики-нолики» (игрок против ИИ) с системой монет, случайным дропом и двумя уровнями сложности.  
Реализована на чистом JavaScript + Canvas без внешних библиотек.

## 🎮 Игровой процесс

- Игрок – **X**, ИИ – **O**.
- Игрок ходит первым.
- Цель – собрать линию из трёх своих символов.

## 💰 Экономика и риск

- Начальный баланс: **100 монет**.
- **Победа игрока**: +10 монет + случайный бонус от 1 до 20 монет.
- **Поражение игрока**: –5 монет (баланс не уходит ниже 0).
- **Ничья**: баланс не меняется.
- Статистика побед/поражений/ничьих сохраняется на протяжении сессии.

## 🧠 Уровни сложности

- **Лёгкая** – ИИ ходит **случайно**.
- **Сложная** – ИИ использует алгоритм:  
  1. Если может выиграть – выигрывает.  
  2. Иначе блокирует победу игрока.  
  3. Иначе занимает центр.  
  4. Иначе случайный угол.  
  5. Иначе случайная клетка.

## 🚀 Запуск

Скачайте `index.html` и откройте в любом современном браузере (Chrome, Firefox, Edge).  
Никакого сервера не требуется.

## 📁 Репозиторий

[https://github.com/ваш-аккаунт/tic-tac-toe-ai](https://github.com/ваш-аккаунт/tic-tac-toe-ai) — замените на реальную ссылку.

## 🧩 UML-диаграмма классов

```mermaid
classDiagram
    class Game {
        -board: string[]
        -gameActive: boolean
        -isPlayerTurn: boolean
        -playerScore: int
        -aiScore: int
        -drawScore: int
        -coins: int
        +makeMove(index, symbol)
        +checkWinnerOnBoard()
        +endGame(result)
        +resetGame()
    }
    class BoardRenderer {
        +draw(board, winningLine)
        +highlightLine(line)
    }
    class AIPlayer {
        -difficulty: string
        +getMove(board, difficulty)
        +smartAIMove()
        +easyAIMove()
    }
    class RewardSystem {
        +applyReward(result, coins)
        +getRandomBonus()
    }
    Game --> BoardRenderer
    Game --> AIPlayer
    Game --> RewardSystem