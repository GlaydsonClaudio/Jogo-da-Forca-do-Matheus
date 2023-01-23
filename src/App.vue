<script setup>
import { ref, computed, watch } from 'vue'
import HeaderForca from './components/HeaderForca.vue';
import ImageForca from './components/ImageForca.vue';
import WordForca from './components/WordForca.vue';
import KeyboardForca from './components/KeyboardForca.vue';
import Restart from './components/Restart.vue';
import NotificationWinner from './components/NotificationWinner.vue';

const words = [
   'GLAYDSON',
   'RARINE',
   'MATHEUS',
   'JOAO',
   'PEDRO'
];

function choiceWord()
{
  return words[Math.floor(Math.random() * words.length)];
}

let secretWord = choiceWord();

const right = ref([]);
const wrong = ref([]);
const errors = computed(() => wrong.value.length);
const rightComputed = computed(() => right.value.length);

function lettersIn(inWord)
{
    inWord = inWord.split('');
    let withoutRepeat = inWord.filter((el, i) => inWord.indexOf(el) === i);
    console.log(withoutRepeat);
    return withoutRepeat.length;
}

let lettersInSecretWord = lettersIn(secretWord);

const playing = ref(true);
watch([errors,rightComputed],() => {
    console.log(errors.value)
    console.log(lettersInSecretWord)
    console.log(rightComputed.value)
    playing.value = (errors.value < 6 && rightComputed.value < lettersInSecretWord)
    console.log(playing.value)
    console.log('===========')
  });


function keyPressed(event) {
  if (secretWord.includes(event) && !right.value.includes(event)) {
    right.value.push(event);
  } else if (!wrong.value.includes(event)) {
    wrong.value.push(event);
  }
}

function restart() {
  secretWord = choiceWord();
  lettersInSecretWord = lettersIn(secretWord);
  right.value = [];
  wrong.value = [];
}

</script>

<template>
  <HeaderForca />
  <ImageForca :errors="errors" />
  <WordForca :word="secretWord" :right="right" />
  <KeyboardForca :right="right" :wrong="wrong" @letter-press="keyPressed" v-show="playing" />
  <Restart @restart="restart" v-show="!playing" />
  <NotificationWinner />
</template>

<style lang="scss">
</style>
