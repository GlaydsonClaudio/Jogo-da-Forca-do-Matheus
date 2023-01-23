<template>
    <div class="notification">
        <img src="../assets/winner.png" alt="Você é um Vencedor.">
        <span class="principal">Parabéns</span>
        <span class="secondary">Você venceu.</span>
    </div>
</template>
<style lang="scss">
.notification {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 70vh;
    background-color: hwb(0 0% 100% / 0.7);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;


    & > img {
        width: 90vw;
        margin: 0 auto;
    }

    & .principal {
        font-size: 5.5rem;
    }

    & .secondary {
        font-size: 3rem;
    }
}
</style>