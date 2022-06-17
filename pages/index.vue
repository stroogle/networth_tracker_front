<template>
    <div>
        <p class="text-2xl font-bold">CREATE BEAUTIFUL BALANCE SHEETS FREE</p>
        <ItemList title="Assets" :items="assets" />
        <ItemList title="Liabailities" :items="liabilities" />
        <button disabled class="rounded w-full bg-blue-400 text-white py-2 disabled:bg-gray-300">DOWNLOAD NOW</button>
    </div>
</template>

<script lang="ts">
export default {
    data() {
        return {
            assets: [],
            liabilities: []
        }
    }
}
</script>

<style scoped>
</style>