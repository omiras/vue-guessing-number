<script setup>

import { ref } from 'vue';

// Número a adivinar
const randomNumber = ref(parseInt(Math.random() * 100) + 1)

// Variable de estado nos determina si estamos jugando o no
const isPlaying = ref(false)

// variable para almacenar todos los números que el jugador va probando
const previousGuesses = ref([])

// Número que ha escrito el usuario en el <input>
const currentGuess = ref("")

const startGame = () => {
  console.log("Game Starts")
  isPlaying.value = true
}

const checkGuess = () => {
  // añadir el número que ha pusto en el input el usuario a la variable previousGuesses
  previousGuesses.value.push(currentGuess.value)
  currentGuess.value = ""
}

// En los ficheros SFC, NO hace falta exportar ninguna variable ni función. Están automáticamente disponibles en todo el <template>

// Reto: al hacer clic en el boton, nos "cambia" de pantalla

/**
 * 1. Asignar un escuchador de eventos al botón, para que al hacer click ejecute la función startGame
 * 2. La función startGame debe cambiar la variable de estado isPlaying a true, para indicar que ya estamos jugando
 * 
 * Corregir: 13:26
 */

/**
 * Reto: al introducir un número en el input y hacer click, debe añadirlo a la lista de números ya probados. Vamos a guardar esos datos en un array y lo vamos a inicilizar como []
 * 
 * 1. Añadir la directiva v-model al input. La variable de estado relacionada le podemos llamar currentGuess
 * 2. Cuando el usuario haga click en Check Guess, tenemos que añadir el número a la variable previousGuesses. Vais a tener que crear una función nueva para gestionar el click de ese botón
 * 3. Mostrar en la parte adecuada del <template> todos los números que ya ha probado el usuario. NO hace falta computed properties (podríais usarla), simplemente usad la notación mostacho {{ }} para mostrar la variable previousGuessses
 * 4. BONUS ORIOL: Crear una variable de estado con el número a adivinar entre 1 y 100.
 * 
 * Coregir: 13:50
 */

</script>

<template>
  <main>
    <h2>Number guessing game</h2>

    <section v-if="isPlaying">
      <p>Try and guess a random number between 1 and 100.</p>
      <p>You have 10 attempts to guess the right number.</p>
      <div id="wrapper">
        <label for="guessField">Guess a number</label>
        <input v-model="currentGuess" type="number" id="guessField">
        <button @click="checkGuess" class="button-check">Check Guess</button>

        <div class="resultParas">
          <p>Previous Guesses: <span class="guesses"> {{ previousGuesses.join("-") }}</span></p>
          <p>Guesses Remaining: <span class="lastResult">10</span></p>
          <p class="lowOrHi"></p>
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
