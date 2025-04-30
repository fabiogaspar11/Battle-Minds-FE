<template>
  <div class="tic-tac-toe">
    <h2>Tic Tac Toe (AI Impossible)</h2>
    <div class="board">
      <div v-for="(cell, index) in board" :key="index"
           class="cell"
           @click="handleClick(index)">
        {{ cell }}
      </div>
    </div>
    <p v-if="winner">{{ winnerMessage }}</p>
    <button @click="resetGame">Restart</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const board = ref(Array(9).fill(''))
const player = 'O'
const ai = 'X'
const winner = ref(null)

const handleClick = (index) => {
  if (board.value[index] || winner.value) return

  board.value[index] = player
  if (checkWin(board.value, player)) {
    winner.value = player
    return
  }

  if (!board.value.includes('')) return

  const bestMove = getBestMove()
  board.value[bestMove] = ai
  if (checkWin(board.value, ai)) {
    winner.value = ai
  }
}

const resetGame = () => {
  board.value = Array(9).fill('')
  winner.value = null
}

const winnerMessage = computed(() =>
  winner.value === 'O' ? 'You win!' :
  winner.value === 'X' ? 'AI wins!' : ''
)

function checkWin(b, player) {
  const winCombos = [
    [0,1,2], [3,4,5], [6,7,8],
    [0,3,6], [1,4,7], [2,5,8],
    [0,4,8], [2,4,6]
  ]
  return winCombos.some(combo => combo.every(i => b[i] === player))
}

function getBestMove() {
  let bestScore = -Infinity
  let move
  for (let i = 0; i < 9; i++) {
    if (board.value[i] === '') {
      board.value[i] = ai
      let score = minimax(board.value, 0, false)
      board.value[i] = ''
      if (score > bestScore) {
        bestScore = score
        move = i
      }
    }
  }
  return move
}

function minimax(b, depth, isMaximizing) {
  if (checkWin(b, ai)) return 10 - depth
  if (checkWin(b, player)) return depth - 10
  if (!b.includes('')) return 0

  if (isMaximizing) {
    let best = -Infinity
    for (let i = 0; i < 9; i++) {
      if (b[i] === '') {
        b[i] = ai
        best = Math.max(best, minimax(b, depth + 1, false))
        b[i] = ''
      }
    }
    return best
  } else {
    let best = Infinity
    for (let i = 0; i < 9; i++) {
      if (b[i] === '') {
        b[i] = player
        best = Math.min(best, minimax(b, depth + 1, true))
        b[i] = ''
      }
    }
    return best
  }
}
</script>

<style scoped>
.tic-tac-toe {
  width: 48%;
  min-width: 280px;
  background: #f3f3f3;
  border-radius: 8px;
  padding: 16px;
  text-align: center;
}

.board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 6px;
  margin: 12px 0;
}

.cell {
  width: 60px;
  height: 60px;
  background: #fff;
  border: 2px solid #ccc;
  font-size: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

button {
  padding: 6px 12px;
  border: none;
  background: #333;
  color: white;
  border-radius: 4px;
  cursor: pointer;
}
</style>
