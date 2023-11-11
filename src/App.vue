<script setup>

import { ref } from 'vue';

const isPlaying = ref(false)
const randomNumber = ref(0)
const previousGuesses = ref([])
const currentGuess = ref("")
const attempts = ref(3)

const startGame = () => {
  console.log("Game Starts")
  randomNumber.value = parseInt(Math.random() * 100) + 1
  console.log("Game to guess: ", randomNumber.value)
  isPlaying.value = true;
}

const checkGuess = () => {
  console.log("Check guess: ", currentGuess.value, randomNumber.value)
  previousGuesses.value.push(currentGuess.value)
  currentGuess.value = ""
  attempts.value--
}
</script>

<template>
  <main>
    <h2>Number guessing game</h2>

    <section v-if="isPlaying">
      <p>Try and guess a random number between 1 and 100.</p>
      <p>You have 10 attempts to guess the right number.</p>
      <div id="wrapper">
        <div>
          <label for="guessField">Guess a number</label>
          <input v-model="currentGuess" type="number" id="guessField" class="guessField">
          <button @click="checkGuess"
            :disabled="attempts == 0 || previousGuesses[previousGuesses.length - 1] == randomNumber"
            class="button-check">Check Number</button>
        </div>
        <div v-show="previousGuesses.length != 0">
          <p>Previous Guesses: <span>{{ previousGuesses.join("-") }}</span></p>
          <p>Guesses Remaining: <span class="lastResult"> {{ attempts }}</span></p>
          <p v-if="attempts == 0 && previousGuesses[previousGuesses.length - 1] != randomNumber"> YOU LOST 🤧</p>
          <p style="color: red" v-else-if="previousGuesses[previousGuesses.length - 1] > randomNumber"> Correct number is
            lower
          </p>
          <p style="color: green" v-else-if="previousGuesses[previousGuesses.length - 1] < randomNumber"> Correct number
            is
            higher</p>
          <p v-else-if="previousGuesses[previousGuesses.length - 1] == randomNumber" style="font-size: 48px;">You Won!!
            Correct number was {{
              randomNumber }} </p>
        </div>
      </div>
    </section>
    <section v-else>
      <button @click="startGame">Start Game</button>
    </section>
  </main>
</template>

<style>
.button-check {
  background-color: rgb(128, 70, 128);
}
</style>
