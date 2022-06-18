<script setup lang="ts">
const currency = useCurrency();
</script>

<template>
    <div class="flex items-center space-x-4">
        <span>Currency Symbol:</span>
        <input class="inputs" type="text" v-model="currency"/>
    </div>
</template>

<script lang="ts">
    
    export default {
        data(){
            return {

            }
        }
    }
</script>

<style scoped>
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

input:invalid {
    background: red;
}

.inputs {
    @apply h-[38px] bg-gray-100 rounded outline-none px-4 w-[42px] text-center;
}
</style>