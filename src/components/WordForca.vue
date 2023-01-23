<script setup>
const props = defineProps(['word','right']);
</script>
<template>
<section class="word-forca" >
    <div class="word" v-for="letter in word">
        <span v-show="right.includes(letter)">{{ letter }}</span>
    </div>
</section>
</template>
<style lang="scss">
.word-forca {
    height: 10vh;
    display: flex;
    padding-bottom: 12px;
    
    & .word {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
        margin: 0 5px;
        border-bottom: solid 3px #000000;
    }
}
</style>