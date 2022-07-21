<template>
    <label class="cursor-pointer">
        <input :value="modelValue" @input="toggle" type="checkbox" name="switch" class="hidden">
        <div :class="`w-9 p-0.5 rounded-full transition-all ease-in duration-100 ${isOn ? on : off}`">
            <div :class="`h-4 w-4 bg-white rounded-full transition-all ease-out duration-150 relative ${isOn ? onCircle : offCircle}`"></div>
        </div>
    </label>
</template>

<script lang="ts">

export default defineComponent({
    data(){
        return {
            off: "bg-gray-300",
            on: "bg-green-400",
            onCircle: "ml-4",
            offCircle: "ml-0",
            isOn: this.modelValue
        }
    },
    props: ['modelValue'],
    emits: ['update:modelValue'],
    methods: {
        toggle(e){
            this.$emit('update:modelValue', e.target.checked);
            this.isOn = !this.isOn;
        }
    }
})
</script>

<style scoped>

</style>