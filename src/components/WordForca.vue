<script setup>
const props = defineProps(['word','right']);
const tip = '1 palavra com ' + props.word.length + ' letras';
</script>
<template>
<section class="word-forca" >
    <div class="tip">{{ tip }}</div>
    <div class="word">
        <div 
            class="letter" 
            :class="{ 'key': letter !== ' '} " 
            v-for="letter in word"
        >
            <span v-show="right.includes(letter)">{{ letter }}</span>
        </div>
    </div>
</section>
</template>
<style lang="scss">
.word-forca {
    height: 10vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    & .tip {
        display: flex;
        justify-content: center;
        font-size: 1.5rem;
    }

    & .word {
        display: flex;
        padding-bottom: 10px;
        
        & .letter {
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            margin: 0 3px;
            
            &.key {
                border-bottom: solid 2px black;
            }
        }

    }

}
</style>