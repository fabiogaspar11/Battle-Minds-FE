<script setup>
import TwitchPlayer from "./components/TwitchPlayer.vue";
</script>

<template>
  <div id="app">
    <h1 class="app-title">Battle Minds</h1>

    <TwitchPlayer />

    <ul class="ai-team">
      <li>Beatriz Francisco</li>
      <li>Fábio Gaspar</li>
      <li>Joana Oliveira</li>
      <li>Rita Gonçalves</li>
    </ul>
    <div class="blocks-container">
      <!-- Blocks go here -->
    </div>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap");

body {
  background-image: url("/public/background3.png"); /* no need for /public prefix */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Orbitron", sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 10px;
  text-align: center;
}

.app-title {
  font-size: 48px;
  color: #00ffff;
  text-shadow: 2px 2px 10px #000;
  margin: 20px 0; /* Reduced margin to give less space */
  display: block;
  background-color: rgba(0, 255, 255, 0.5); /* Transparent background for title */
  border-radius: 8px;
  padding: 10px;
}

.blocks-container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 20px;
}

.ai-team {
  margin-top: 20px;
  list-style: none;
  padding: 0;
  margin-bottom: 40px;
  font-size: 25px; /* Increased font size for better readability */
  color: black;
  font-weight: 800; /* More bold than just "bold" */
  font-family: 'Orbitron', sans-serif;
  background-color: rgba(255, 255, 255, 0.7); /* Slightly less transparent for better contrast */
  border-radius: 8px;
  padding: 15px;
  display: inline-block;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); /* Added text shadow for contrast */
}


.ai-team li {
  margin: 4px 0;
}
</style>
