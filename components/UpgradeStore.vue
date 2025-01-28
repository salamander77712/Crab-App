<script setup lang="ts">
</script>

<template>
    <h3>Upgrades</h3>
    <UpgradeButton description="Catch more crabs" :cost="1" :cost-increase="1.5" variable="catchingPower" />
    <h3>Unlocks</h3>
    <UnlockButton description="Unlock Crab Breeding" :cost=5 unlock-state="breedingUnlocked"/>
</template>

<style scoped>
</style>