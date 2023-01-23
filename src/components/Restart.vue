<template>
<section class="restart">
    <button @click="$emit('restart')">Reiniciar</button>
</section>
</template>
<style lang="scss">
.restart {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 35vh;

    & > button {
        background-color: #d3d3d3;
        border: solid 1px #808080;
        color: #404040;
        font-size: 3rem;
        padding: 1rem;
        border-radius: 1rem;
    }
}
</style>