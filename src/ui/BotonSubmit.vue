<template>
    <button class="amarillo m-2" :to="anyProps.link">
        <slot></slot>
        <span></span><span></span><span></span><span></span>
    </button>

</template>

<script setup>
import {defineProps} from "vue";
const anyProps = defineProps({
    link: String
});

</script>


<style scoped>

button {
    --c: goldenrod;
    color: var(--c);
    font-size: 16px;
    border: 0.3em solid var(--c);
    border-radius: 0.5em;
    width: 12em;
    height: 3em;
    text-transform: uppercase;
    font-weight: bold;
    font-family: sans-serif;
    letter-spacing: 0.1em;
    text-align: center;
    line-height: 2em;
    position: relative;
    overflow: hidden;
    z-index: 1;
    transition: 0.5s;
    margin: 1em;
}

button span {
    position: absolute;
    width: 25%;
    height: 100%;
    background-color: var(--c);
    transform: translateY(150%);
    border-radius: 50%;
    left: calc((var(--n) - 1) * 25%);
    transition: 0.5s;
    transition-delay: calc((var(--n) - 1) * 0.1s);
    z-index: -1;
}

button:hover {
    color: black;
}

button:hover span {
    transform: translateY(0) scale(2);
}

button span:nth-child(1) {
    --n: 1;
}

button span:nth-child(2) {
    --n: 2;
}

button span:nth-child(3) {
    --n: 3;
}

button span:nth-child(4) {
    --n: 4;
}
</style>