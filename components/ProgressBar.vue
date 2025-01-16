<script setup lang="ts">
defineProps({
  animationState: String,
})
</script>

<template>
<div class="outer"><div  :class="animationState"></div></div>
</template>

<style scoped>
div {
    border-radius: 25px;
    height: 20px;
}
div.outer {
    border-style: solid;
}
@keyframes progress {
    from {width: 0%;}
    to {width: 100%;}
}
div.initial {
    width: 0%;
}
div.running {
    background-color: blue;
    animation-name: progress;
    animation-duration: 1s;
    animation-timing-function: linear;
}
</style>