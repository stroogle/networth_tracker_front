<template>
    <div class="grid grid-cols-1 gap-y-4">
        <h1 class="text-base font-bold">{{title}}</h1>
        <Item1 v-for="(item, idx) in items"
            :key="idx"
            :itemName="item.name"
            :itemValue="item.value"
            :doThis="removeItem"
            :idx="idx"
        />
        <div class="grid grid-cols-2 gap-x-4">
            <input class="inputs" v-model="name" type="text" placeholder="Label"/>
            <input class="inputs" v-model="value" type="number" name="" id="" placeholder="0">
        </div>
        
        <button class="w-full py-2 text-white bg-green-400 rounded flex justify-center items-center" @click="addItem">Add {{title}}</button>
    </div>
</template>

<script lang="ts">
import Item1 from './Item.vue';
export default {
    props: {
        items: {
            default: [],
            required: true,
        },
        title: {
            default: "bruh"
        }
    },
    data() {
        return {
            name: "",
            value: null
        };
    },
    methods: {
        addItem(): void {
            if (this.name == "" || this.value < 1)
                return;
            this.items.push({
                name: this.name,
                value: this.value,
            });
            this.name = "";
            this.value = null;
        },
        removeItem(idx: number): void {
            this.items.splice(idx, 1);
        }
    },
    components: { Item1 }
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
    @apply h-[38px] bg-gray-100 rounded outline-none px-4;
}
</style>