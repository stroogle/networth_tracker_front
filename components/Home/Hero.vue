<template>
    <header class="heroContainer">
        <div class="overlay"></div>
        <article class="heroMessage">
            <h2 class="text-green-400 text-2xl">Find Your Net Worth</h2>
            <h1 class="text-5xl text-white">Generate a Balance Sheet.</h1>
            <HomeBreakLine />
            <p class="text-base text-white">A free tool to help you generate beautiful balance sheets that are exported as pdf documents.</p>
            <nav class="flex gap-x-4">
                <a href="#tool">
                    <Button type="primary">Get Started</Button>
                </a>
                <a href="#about">
                    <Button type="secondary">About Us</Button>
                </a>
            </nav>
        </article>
    </header>
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

.heroMessage {
    @apply w-full grid grid-cols-1 gap-y-4 px-8 z-10 max-w-7xl mx-auto;
}

.overlay {
    @apply absolute z-0 top-0 left-0 w-full h-full bg-black opacity-50 px-8 flex flex-col justify-around;
}

.heroContainer {
    @apply w-full h-[648px] relative flex flex-col justify-around;
    background-image: url("/heroImage.jpeg");
    background-position: center;
    background-size: cover;
}

</style>