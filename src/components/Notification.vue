<script setup>
const props = defineProps(['winner']);
</script>
<template>
<div class="notification" v-if="winner">
    <img src="../assets/winner.png" alt="Você é um Vencedor.">
    <span class="principal">Parabéns</span>
    <span class="secondary">Você venceu.</span>
</div>
<div class="notification" v-else>
    <img src="../assets/loser.png" alt="Você é um Vencedor.">
    <span class="principal">Que pena!</span>
    <span class="secondary">Não foi desta vez.</span>
</div>
</template>
<style lang="scss">
.notification {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 70vh;
    background-color: #ffffffcc;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;


    & > img {
        width: 90vw;
        margin: 0 auto;
    }

    & .principal {
        font-size: 5rem;
    }

    & .secondary {
        font-size: 3rem;
    }
}
</style>