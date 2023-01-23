<script setup>
import { ref, computed } from 'vue'
import HeaderForca from './components/HeaderForca.vue';
import ImageForca from './components/ImageForca.vue';
import WordForca from './components/WordForca.vue';
import KeyboardForca from './components/KeyboardForca.vue';

const right = ref([]);
const wrong = ref([]);
const errors = computed(() => wrong.value.length);
const secretWord = 'GLAYDSON';

function keyPressed(event) {
  if (secretWord.includes(event) && !right.value.includes(event)) {
    right.value.push(event);
  } else if (!wrong.value.includes(event)) {
    wrong.value.push(event);
  }
}

</script>

<template>
  <HeaderForca />
  <ImageForca :errors="errors" />
  <WordForca :word="secretWord" :right="right" />
  <KeyboardForca :right="right" :wrong="wrong" @letter-press="keyPressed" v-show="errors<6"/>
</template>

<style lang="scss">
</style>
