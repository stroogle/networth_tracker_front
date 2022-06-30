<template>
    <div :class="buttonStyle">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup () {
        

        return {
            buttonStyle: "uppercase px-4 py-2 text-white rounded inline-block cursor-pointer transition duration-150"
        }
    },
    props: ['type'],
    created(){
        let message: string = ""
        switch(this.type) {
            case "primary":
                message += "bg-green-400 hover:bg-green-500"
                break;
            case "secondary":
                message += "border-green-400 border-2 bg-transparent hover:bg-green-400 px-[14px] py-[6px]"
                break;
            default:
                message += "bg-green-400 hover:bg-green-500"
                break;
        }
        this.buttonStyle += ` ${message}`
    }
})
</script>

<style scoped>

</style>