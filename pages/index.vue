<template>
    <div class="mainContainer">
        <HomeHero />
        <HomeAbout />
        <HomeTool />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    data(){
        return {}
    }
})
</script>

<style scoped>

.mainContainer {
    @apply grid grid-cols-1 gap-y-16 justify-around;
}

</style>