<script setup lang="ts">
const crabs:Ref = useState('crabs', () => 0);
const money:Ref = useState('money', () => 0);
let caughtCrab:boolean = false;
watch(
  crabs,
  () => {
    caughtCrab = true;
  },
  { once: true }
)
</script>

<template>
<div>
    <p>You have {{ crabs }} crabs</p>
    <p v-if="caughtCrab" class="animate-in">You have ${{ money.toFixed(2) }}</p>
</div>
<div class="section">
    <CrabCatchButton />
</div>
<div v-if="caughtCrab" class="section animate-in">
    <CrabSellButton />
</div>
</template>

<style scoped>
p {
    color: red;
}
div.section {
    float: left;
    width: 15%;
    border-radius: 25px;
    background-color: lightblue;
    height: 100px;
    margin-right: 10px;
    padding: 10px;
}
@keyframes fade-in{
    from {opacity: 0;}
    to {opacity: 1;}
}
.animate-in {
    animation-name: fade-in;
    animation-duration: 1s;
}
</style>