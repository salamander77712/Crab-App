<script setup lang="ts">
const crabs:Ref = useState('crabs');
const money:Ref = useState('money');
const minPrice:number = 0.5;
const maxPrice:number = 1.5;
const maxChange:number = 0.03;
const priceChangeInterval:number = 1000;
let sellPrice:Ref = ref(minPrice);
function changePrice(){
    sellPrice.value += (Math.random() * 2 * maxChange) - maxChange;
    if(sellPrice.value < minPrice){
        sellPrice.value = minPrice;
    }
    else if(sellPrice.value > maxPrice){
        sellPrice.value = maxPrice;
    }
    console.log(sellPrice.value)
}
onMounted(()=> setInterval(changePrice, priceChangeInterval));
function sellCrab(){
    if(crabs.value >= 1){
        crabs.value--;
        money.value += sellPrice.value;
    }
}
</script>

<template>
<button @click="sellCrab">Sell 1 crab for ${{ sellPrice.toFixed(2) }}</button>
</template>

<style scoped>
button {
    border-radius: 15px;
    margin-bottom: 5px;
    border-width: 1px;
}
</style>