<template>
    <div class="grid grid-cols-1 gap-y-4">
        <p class="text-2xl font-bold">CREATE BEAUTIFUL BALANCE SHEETS FREE</p>
        <CurrencySelector />
        <ItemList title="Assets" :items="assets" />
        <ItemList title="Liabailities" :items="liabilities" />
        <button :disabled="!downloadReady" class="rounded w-full bg-blue-400 click:bg-blue-500 text-white py-2 disabled:bg-gray-300">DOWNLOAD NOW</button>
    </div>
</template>

<script lang="ts">
export default {
    data() {
        return {
            assets: [],
            liabilities: [],
            assetTotal: 0,
            liabilityTotal: 0,
            downloadReady: false
        }
    },
    watch: {
        assets: {
            handler(){
                this.assetTotal = this.assets.reduce((pV, cV) => pV + cV.value, 0)
                if(this.assetTotal > 0)
                    this.downloadReady = true;
                else
                    this.downloadReady = false;
            },
            deep: true
        },
        liabilities: {
            handler(){
                this.liabilityTotal = this.liabilities.reduce((pV, cV) => pV + cV.value, 0)
            },
            deep: true
        }
    }
}
</script>

<style scoped>
</style>