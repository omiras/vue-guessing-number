<script setup>

import { ref } from 'vue';

const isPlaying = ref(false)

const startGame = () => {
  console.log("Game Starts")
}


</script>

<template>
  <main>
    <h2>Number guessing game</h2>

    <section v-if="isPlaying">
      <p>Try and guess a random number between 1 and 100.</p>
      <p>You have 10 attempts to guess the right number.</p>
      <div id="wrapper">
        <label for="guessField">Guess a number</label>
        <input type="number" id="guessField">
        <button class="button-check">Check Guess</button>

        <div class="resultParas">
          <p>Previous Guesses: <span class="guesses"></span></p>
          <p>Guesses Remaining: <span class="lastResult">10</span></p>
          <p class="lowOrHi"></p>
        </div>
      </div>
    </section>
    <section v-else>
      <button>Start Game</button>
    </section>
  </main>
</template>

<style>
.button-check {
  background-color: rgb(128, 70, 128);
}
</style>
