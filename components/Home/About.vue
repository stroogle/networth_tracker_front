<template>
    <article id="about" class="aboutContainer">
        <div class="leftContainer">
            <h2 class="text-2xl text-green-400 font-bold">About Us</h2>
            <h1 class="text-black text-5xl">Find Your Net Worth</h1>
            <HomeBreakLine />
        </div>
        <section class="rightContainer">
            <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas gravida cursus eleifend. Nullam ornare sapien quis vulputate cursus. Vivamus vel pellentesque purus, sed dignissim elit. Maecenas ac augue metus. Suspendisse in elit nibh. Vestibulum in nibh risus. Phasellus ut cursus sem. Vestibulum feugiat eros lorem, vitae faucibus arcu aliquam ac. Sed tempor, arcu non sodales gravida, sapien dui iaculis felis, vel luctus sapien nisi non orci. Ut laoreet ante tellus, vel hendrerit lorem tincidunt sed. Etiam rhoncus euismod velit ac rutrum.
            </p>
            <p>
                Donec porttitor turpis eu mi tempus facilisis. Maecenas id ullamcorper elit, quis tempus enim. In dignissim dolor in accumsan tincidunt. Donec vel diam vitae risus elementum congue. Cras varius, enim vitae condimentum mattis, erat lacus.
            </p>
            <NuxtLink target="_blank" to="https://www.buymeacoffee.com/colm">
                <Button type="primary" class="w-full text-center lg:w-fit">Donate Now</Button>
            </NuxtLink>
        </section>
    </article>
</template>

<script setup lang="ts">

</script>

<style scoped>

.aboutContainer {
    @apply max-w-7xl px-8 grid grid-cols-1 gap-y-4 gap-x-4 lg:grid-cols-2 w-full mx-auto;
}

.leftContainer {
    @apply flex flex-col gap-y-4;
}

.rightContainer {
    @apply flex flex-col gap-y-4 text-justify lg:text-left;
}

</style>