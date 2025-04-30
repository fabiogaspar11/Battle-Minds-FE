<template>
  <div class="ai-chat">
    <h2>Ask an AI</h2>
    <div class="chat-box">
      <div v-for="(message, index) in messages" :key="index" class="message">
        <strong>{{ message.from }}:</strong> {{ message.text }}
      </div>
    </div>
    <input v-model="input" @keydown.enter="sendMessage" placeholder="Ask something..." />
    <button @click="sendMessage">Send</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const input = ref('')
const messages = ref([])

const sendMessage = () => {
  if (!input.value.trim()) return

  messages.value.push({ from: 'You', text: input.value })

  // Fake AI response
  setTimeout(() => {
    messages.value.push({ from: 'AI', text: generateAiResponse(input.value) })
  }, 500)

  input.value = ''
}

const generateAiResponse = (text) => {
  if (text.toLowerCase().includes('tictactoe')) return "It's unbeatable!"
  if (text.toLowerCase().includes('ai')) return "AI is rapidly evolving."
  return "I'm not sure, but that's interesting!"
}
</script>

<style scoped>
.ai-chat {
  width: 48%;
  min-width: 280px;
  background: #f3f3f3;
  border-radius: 8px;
  padding: 16px;
  text-align: left;
}

.chat-box {
  background: #fff;
  height: 200px;
  overflow-y: auto;
  padding: 8px;
  border: 1px solid #ccc;
  margin-bottom: 10px;
  border-radius: 4px;
}

.message {
  margin-bottom: 6px;
}

input {
  width: 70%;
  padding: 6px;
  margin-right: 6px;
  border-radius: 4px;
  border: 1px solid #aaa;
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
