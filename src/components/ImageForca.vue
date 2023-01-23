<script setup>
const props = defineProps(['errors']);
</script>
<template>
<section class="image-forca">
    <svg viewBox="0 0 130 150" xmlns="http://www.w3.org/2000/svg" style="fill:#000000">
        <g style="fill:none;stroke:#000000;stroke-width:1;" v-show="errors>=1">
            <circle cx="105" cy="47" r="15" />
            <rect width="1" height="7" x="105" y="25" />
        </g>
        <rect width="1" height="50" x="105" y="62" v-show="errors>=2" />
        <rect width="1" height="35" x="124" y="-25" transform="rotate(45)" v-show="errors>=3" />
        <rect width="1" height="35" x="24" y="124" transform="rotate(-45)" v-show="errors>=4" />
        <rect width="1" height="35" x="147" y="44" transform="rotate(30)" v-show="errors>=5" />
        <rect width="1" height="35" x="35" y="150" transform="rotate(-30)" v-show="errors>=6" />
        <g v-show="errors>=7">
            <rect width="1" height="10" x="38" y="97" transform="rotate(-45)" />
            <rect width="1" height="10" x="101" y="-43" transform="rotate(45)" />
            <rect width="1" height="10" x="47" y="106" transform="rotate(-45)" />
            <rect width="1" height="10" x="110" y="-52" transform="rotate(45)" />
        </g>
        <g style="fill:#803300">
            <rect width="70" height="10" x="35" y="0" />
            <rect width="10" height="25" x="100" y="0" />
            <rect width="10" height="150" x="35" y="0" />
            <rect width="80" height="10" x="0" y="140" />
            <rect width="40" height="10" x="-95" y="105" transform="rotate(-45)" />
            <rect width="40" height="10" x="109" y="49" transform="rotate(45)" />
        </g>
    </svg>
</section>
</template>
<style lang="scss">
.image-forca {
    height: 45vh;
    display: flex;
    justify-content: center;
    
    & svg {
        height: 100%;
    }
}
</style>