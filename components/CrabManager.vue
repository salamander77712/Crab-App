<script setup lang="ts">
const crabs:Ref = useState('crabs', () => 0);
const money:Ref = useState('money', () => 0);
</script>

<template>
<div>
    <p>You have {{ crabs }} crabs</p>
    <p>You have ${{ money.toFixed(2) }}</p>
</div>
<div class="section">
<CrabCatchButton />
</div>
<div class="section">
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
</style>