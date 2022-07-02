<template>
    <div id="tool" class="toolContainer">
        <div class="leftSide">
            <p class="text-2xl text-green-400 font-bold">Tool</p>
            <p class="text-black text-5xl">How it Works</p>
            <HomeBreakLine />
        </div>
        <div class="rightSide">
            <HomeToolComp />
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup () {
        

        return {}
    }
})
</script>

<style scoped>

.toolContainer {
    @apply grid grid-cols-1 gap-y-4 gap-x-4 px-8 max-w-7xl lg:grid-cols-2 w-full mx-auto;
}

.leftSide {
    @apply flex flex-col gap-y-4;
}

</style>