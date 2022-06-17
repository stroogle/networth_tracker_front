<template>
    <div>
        <h1>{{title}}</h1>
        <div v-for="(item, idx) in items" :key="idx" class="flex justify-between">
            <p @click="removeItem(idx)">x</p>
            <p>{{item.name}}</p>
            <p>${{item.value}}</p>
        </div>
        <div class="grid grid-cols-2 gap-4">
            <input class="inputs" v-model="name" type="text" placeholder="Label"/>
            <input class="inputs" v-model="value" type="number" name="" id="" placeholder="0">
        </div>
        
        <button class="w-full mt-4 py-2 text-white bg-green-400 rounded flex justify-center items-center" @click="addItem">Add {{title}}</button>
        <p>Total: ${{total}}</p>
    </div>
</template>

<script lang="ts">
import {PropType} from 'vue'
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
            value: null,
            total: 0
        }
    },
    methods: {
        addItem(): void {
            if(this.name == "" || this.value < 1)
                return;
            this.items.push({
                name: this.name,
                value: this.value,
            })
            this.name = "";
            this.value = null;
        },
        removeItem(idx: number): void {
            this.items.splice(idx, 1);
        }
    },
    watch: {
        items: {
            handler(val, oldVal){
                let sum: number = 0;
                for(let i = 0; i < val.length; i++) {
                    sum += this.items[i].value;
                }
                this.total = sum;
            },
            deep: true,
        }
    }
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