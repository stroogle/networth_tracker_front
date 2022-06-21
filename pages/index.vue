<script setup lang="ts">
const {apiBase} = useRuntimeConfig().public
useHead({
    title: "Check My Net Worth"
})
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-2 md:gap-x-4 gap-y-4">
        <p class="text-2xl font-bold md:col-span-2">CREATE BEAUTIFUL BALANCE SHEETS FREE</p>
        <CurrencySelector class="md:col-span-2" />
        <ItemList class="col-span-1" title="Assets" :items="assets" />
        <ItemList class="col-span-1" title="Liabailities" :items="liabilities" />
        <button
            @click="downloadPdf"
            :disabled="!downloadReady"
            class="col-span-1 md:col-span-2 rounded w-full bg-blue-400 click:bg-blue-500 text-white py-2 disabled:bg-gray-300"
        >
            {{downloadMessage}}
        </button>
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
            downloadReady: false,
            downloadMessage: "GENERATE PDF"
        }
    },
    methods: {
        async downloadPdf(){
            this.downloadMessage = "Loading..."
            const body = {
                assets: this.assets,
                liabilities: this.liabilities
            }

            const data: any = await $fetch(`${this.apiBase}/pdf/create`, {
                method: 'POST',
                body
            })
            .catch(e => e.data)
            .finally(() => {
                this.downloadMessage = "GENERATE PDF"
            })

            if(data.error)
                return;


            window.open(`${this.apiBase}/pdfs/${data.filename}`, '_blank');
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
    },
    mounted(){
        this.downloadReady = this.assets.length > 0;
    }
}
</script>

<style scoped>
</style>