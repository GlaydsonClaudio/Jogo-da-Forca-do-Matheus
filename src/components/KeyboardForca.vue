<script setup>
const props = defineProps(['right','wrong']);
const keys = [
    ['A','B','C','D','E','F','G'],
    ['H','I','J','K','L','M'],
    ['N','O','P','Q','R','S','T'],
    ['U','V','W','X','Y','Z']
];
 
// console.log(props.letters);
</script>
<template>
<section class="keyboard-forca">
    <div class="line-keys" v-for="line in keys">
        <button 
            class="keyboard" 
            :class="{ 'success': right.includes(key), 'error': wrong.includes(key) }" 
            v-for="key in line"
            @click="$emit('letter-press',key)"
        >
            {{ key }}
        </button>
    </div>
</section>
</template>
<style lang="scss">
.keyboard-forca {
    height: 35vh;

    & .line-keys {
        height: 25%;
        display: flex;
        justify-content: space-around;

        & .keyboard {
            width: 100%;
            height: 100%;
            background-color: lightgrey;
            border: solid 1px gray;
            font-size: 2rem;
            color: #404040;

            &.success {
                background-color: green;
            }

            &.error {
                background-color: red;
            }
        }
    }
}
</style>