# vue-guessing-number

Implementemos el juego de adivinar un número entre 1 y 100, con el mismo funcionamiento que su versión en JavaScript _vanilla_

Implementa el juego completo en App.vue

Cuando esté funcionando, podemos implementar las siguientes mejoras:

1. Antes de comenzar el juego, podremos elegir el número de intentos y el número máximo a adivinar
2. Calcular el ratio de dificultad. El ratio de difiltar se calcula dividiendo el número máximo a adivinar por el número de intentos. Si es 10-> Dificultad normal. Si es menor, es difícil. En otro caso, se considera un juego fácil
3. Mueve este juego a un componente GuessNumber.vue. Importalo unas cuantas veces en App.vue para comprobar que puedes configurar a jugar a juegos independientes detro de la misma app

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
