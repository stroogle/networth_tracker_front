<script setup lang="ts">
const {apiBase} = useRuntimeConfig().public
useHead({
    title: "Check My Net Worth"
})
const currency = useCurrency();
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
            <span v-if="!getting">{{downloadMessage}}</span>
            <Loader class="" v-else />
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
            downloadMessage: "GENERATE PDF",
            getting: false,
        }
    },
    methods: {
        async downloadPdf(){
            this.getting = true;
            const body = {
                assets: this.assets,
                liabilities: this.liabilities,
                currencySymbol: this.currency
            }

            const data: any = await $fetch(`${this.apiBase}/pdf/create`, {
                method: 'POST',
                body
            })
            .then((data) => {
                this.downloadMessage = "GENERATE PDF"
                return data;
            })
            .catch((e) => {
                this.downloadMessage = "SOMETHING HAPPENED - TRY AGAIN"
                return e.data
            })
            .finally(() => {
                this.getting = false;
            })

            if(!data.filename)
                return;


            window.open(`${this.apiBase}/pdfs/${data.filename}`, '_blank');
        }
    },
    watch: {
        assets: {
            handler(){
                this.assetTotal = this.assets.reduce((pV, cV) => pV + cV.value, 0);
                this.downloadReady = this.assetTotal > 0 && this.liabilityTotal > 0;
            },
            deep: true
        },
        liabilities: {
            handler(){
                this.liabilityTotal = this.liabilities.reduce((pV, cV) => pV + cV.value, 0);
                this.downloadReady = this.assetTotal > 0 && this.liabilityTotal > 0;
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