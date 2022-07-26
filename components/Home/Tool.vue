<template>
    <section id="tool" class="toolContainer">
        <article class="leftSide">
            <h2 class="text-2xl text-green-400 font-bold">Tool</h2>
            <h1 class="text-black text-5xl">How it Works</h1>
            <HomeBreakLine />
            <div class="flex gap-x-4 items-center">
                <Toggle1 v-model="isAdvanced" />
                <p class="text-base text-black">Advanced?</p>
            </div>
        </article>
        <section class="rightSide">
            <HomeToolComp v-if="!isAdvanced" />
            <HomeToolComp v-else advanced />
        </section>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Toggle1 from '../Toggle.vue'

export default defineComponent({
    setup() {
        return {}
    },
    data(){
        return {
            isAdvanced: false
        }
    },
    methods: {
        toggle(){
            this.isAdvanced = !this.isAdvanced;
            return this.isAdvanced;
        }
    },
    components: { Toggle1 }
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