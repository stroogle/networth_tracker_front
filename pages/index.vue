<template>
    <Head>
        <Title>Find My Net Worth</Title>
        <Link rel="icon" type="image/x-icon" href="/favicon.ico"></Link>
        <Html lang="en" />
        <Meta name="description" content="Need help making a balance sheet or figuring out your net position? This free and easy tool to creates reports based on your finance for you." />
        <Meta property="og:type" content="website"/>
        <Meta property="og:url" content="https://findmynetworth.com" />
        <Meta property="og:title" content="Find My Net Worth!" />
        <Meta property="og:description" content="Need help making a balance sheet or figuring out your net position? This free and easy tool to creates reports based on your finance for you." />
        <Meta property="og:image" content="https://findmynetworth.com/heroImage.jpeg" />
        <Meta property="twitter:cart" content="website" />
    </Head>
    <main class="mainContainer">
        <HomeHero />
        <HomeAbout />
        <HomeTool />
    </main>
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