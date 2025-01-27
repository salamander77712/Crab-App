<script setup lang="ts">
const money:Ref = useState('money');
const props = defineProps({
  description: {
    type: String,
    required: true
  },
  cost: {
    type: Number,
    required: true
  },
  unlockState: {
    type: String,
    required: true}
})
const unlockVar:Ref = useState(props.unlockState);
function unlockBreeding () {
    if(money.value >= props.cost){
        unlockVar.value = true;
        money.value -= 5;
    }
}
</script>

<template>
    <button v-if="!unlockVar" @click="unlockBreeding">{{ description }} (${{ cost }})</button>
</template>

<style scoped>
button {
    border-radius: 15px;
    margin-bottom: 5px;;
    border-width: 1px;
}
</style>