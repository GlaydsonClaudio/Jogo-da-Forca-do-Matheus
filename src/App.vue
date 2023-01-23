<script setup>
import { ref, computed } from 'vue'
import HeaderForca from './components/HeaderForca.vue';
import ImageForca from './components/ImageForca.vue';
import WordForca from './components/WordForca.vue';
import KeyboardForca from './components/KeyboardForca.vue';

const right = ref(['A','D','X','G','R','J','E','K']);
const wrong = ref(['Q','P','S','O']);
const errors = computed(() => wrong.value.length);

function teste(event) {
  console.log(event);
}

</script>

<template>
  <HeaderForca />
  <ImageForca :errors="errors" />
  <WordForca />
  <KeyboardForca :right="right" :wrong="wrong" @letter-press="teste"/>
</template>

<style lang="scss">
</style>
