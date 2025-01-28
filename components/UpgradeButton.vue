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
  variable: {
    type: String,
    required: true
  },
  costIncrease: {
    type: Number,
    required: true
  }
});
let currentCost:Ref = ref(props.cost);
const variable:Ref = useState(props.variable);
function upgrade () {
    if(money.value >= currentCost.value){
        variable.value++;
        money.value -= currentCost.value;
        currentCost.value *= props.costIncrease;
        console.log(currentCost);
    }
}
</script>

<template>
    <button @click="upgrade">{{ description }} (${{ currentCost.toFixed(2) }})</button>
</template>

<style scoped>
button {
    border-radius: 15px;
    margin-bottom: 5px;;
    border-width: 1px;
}
</style>