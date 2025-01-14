<script setup lang="ts">
const crabs = useState('crabs', () => 0)
</script>

<template>
<p>You have {{ crabs }} crabs</p>
<CrabCatchButton />
</template>

<style scoped>
p {
    color: red;
}
</style>