<script setup>
import { ref, computed, watch } from 'vue'
import HeaderForca from './components/HeaderForca.vue';
import ImageForca from './components/ImageForca.vue';
import WordForca from './components/WordForca.vue';
import KeyboardForca from './components/KeyboardForca.vue';
import Restart from './components/Restart.vue';
import Notification from './components/Notification.vue';

const words = [
  'AMARELO',
  'AMIGA',
  'AMOR',
  'AVE',
  'BOLO',
  'BRANCO',
  'CAMA',
  'CANECA',
  'CELULAR',
  'CLUBE',
  'COPO',
  'DOCE',
  'ELEFANTE',
  'ESCOLA',
  'ESTOJO',
  'FACA',
  'FOTO',
  'GARFO',
  'GELEIA',
  'GIRAFA',
  'JANELA',
  'JOAO',
  'LIMONADA',
  'MATHEUS',
  'MEIA',
  'NOITE',
  'OVO',
  'PAI',
  'PARQUE',
  'PASSARINHO',
  'PEDRO',
  'PEIXE',
  'PIJAMA',
  'RATO',
  'UMBIGO'
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
    return withoutRepeat.length;
}

let lettersInSecretWord = lettersIn(secretWord);

const playing = ref(true);
watch([errors,rightComputed],() => {
    playing.value = (errors.value < 6 && rightComputed.value < lettersInSecretWord);
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
  <KeyboardForca :right="right" :wrong="wrong" @letter-press="keyPressed" v-if="playing" />
  <Restart @restart="restart" v-if="!playing" />
  <Notification :winner="errors < 6" v-if="!playing" />
</template>