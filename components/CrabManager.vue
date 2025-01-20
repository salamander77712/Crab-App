<script setup lang="ts">
const crabs:Ref = useState('crabs', () => 0);
const money:Ref = useState('money', () => 0);
let caughtCrab:boolean = false;
let madeMoney:boolean = false;
const breedingUnlocked:Ref = useState('breedingUnlocked', () => false);
watch(
  crabs,
  () => {
    caughtCrab = true;
  },
  { once: true }
)
watch(
  money,
  () => {
    madeMoney = true;
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
    <h2>Harvesting</h2>
    <CrabCatchButton />
</div>
<div v-if="caughtCrab" class="section animate-in">
    <h2>Finance</h2>
    <CrabSellButton />
</div>
<div v-if="madeMoney" class="section animate-in">
    <h2>Upgrades</h2>
    <UpgradeStore />
</div>
<div v-if="breedingUnlocked" class="section animate-in">
    <h2>Crab Breeding</h2>
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
    height: 180px;
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