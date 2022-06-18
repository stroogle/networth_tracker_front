<script setup lang="ts">
const currency = useCurrency()
</script>

<template>
    <div class="py-2 px-4 bg-gray-100 rounded flex justify-between text-base">
        <div @click="doThis(idx)">X</div>
        <span>{{itemName}}</span>
        <span>{{currency}}{{itemValue}}</span>
    </div>
</template>

<script  lang="ts">
export default {
    props: ["itemName", "itemValue", "doThis", "idx"]
}
</script>

<style scoped>

</style>