<template>
  <div class="twitch-container">
  <iframe
    src="https://player.twitch.tv/?channel=chapinho&parent=fabiogaspar11.github.io&parent=localhost"
    allowfullscreen>
  </iframe>

  </div>
</template>

<style scoped>
.twitch-container {
  display: flex;
  justify-content: center;
  margin-top: 20px; /* push it down */
}

.twitch-container iframe {
  width: 640px;      /* smaller width */
  height: 360px;     /* smaller height */
  border: none;
  border-radius: 8px;
}

.ai-subtitle {
  font-size: 24px;
  color: #ffffff;
  text-shadow: 1px 1px 5px #00ffff;
  margin-bottom: 10px;
  font-family: 'Orbitron', sans-serif;
}

.ai-team {
  list-style: none;
  padding: 0;
  margin-bottom: 40px;
  font-size: 18px;
  color: #e0e0e0;
  font-family: 'Orbitron', sans-serif;
}

.ai-team li {
  margin: 4px 0;
}
</style>
