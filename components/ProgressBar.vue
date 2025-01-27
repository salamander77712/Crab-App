<script setup lang="ts">
const props = defineProps({
  animationState: {
    type: String,
    required: true
  },
  animationTime: {
    type: Number,
    required: true
    }
})
const cssTime = computed(() => {
    let output:string = (props.animationTime / 1000) + 's'
    return output;
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
    border-width: 1px;
    background-color: white;
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
    animation-duration: v-bind(cssTime);
    animation-timing-function: linear;
    animation-iteration-count: infinite;
}
</style>