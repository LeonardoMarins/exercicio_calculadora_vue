<script setup>
    const porps = defineProps(['entrada','entrada2'])
</script>

<template>
    <input @change="porps.entrada" class="mt-4" type="number"
        placeholder="coloque o valor 1" />
    <input @change="porps.entrada2" class="mt-3" type="number"
        placeholder="coloque o valor 2" />
</template>