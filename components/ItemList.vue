<script setup lang="ts">
const currency = useCurrency()
</script>

<template>
    <form @submit.prevent="addItem" class="grid grid-cols-1 gap-y-4 h-fit">
        <h1 class="text-base font-bold">{{title}}</h1>
        <Item1 v-for="(item, idx) in items"
            :key="idx"
            :itemName="item.name"
            :itemValue="item.value"
            :doThis="removeItem"
            :idx="idx"
        />
        <div class="grid grid-cols-2 gap-x-4 gap-y-4">
            <input ref="nameinput" class="inputs" v-model="name" type="text" placeholder="Label"/>
            <input class="inputs" v-model="value" type="number" name="" id="" :placeholder="`Value (${currency})`">
            <select v-if="advanced" v-model="direction" class="inputs" type="options">
                
                <option :value="1">UP</option>
                <option :value="-1">DOWN</option>
            </select>
            <input v-if="advanced" v-model="rateOfChange" class="inputs" type="number" placeholder="Rate of change" />
        </div>
        
        <button type="submit" class="w-full py-2 text-white bg-green-400 hover:bg-green-500 rounded flex justify-center items-center">Add {{title}}</button>
    </form>
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
        },
        advanced: Boolean
    },
    data() {
        return {
            name: "",
            value: null,
            direction: 1,
            rateOfChange: 0
        };
    },
    methods: {
        addItem(e: Event): void {
            e.preventDefault();
            if (this.name == "" || this.value < 1)
                return;

            const item: any = {
                name: this.name,
                value: this.value,
            }

            console.log("here")

            if(this.advanced) {
                console.log("line 65")
                if(this.direction != 1 && this.direction != -1)
                    return;

                console.log("line 69")

                if(this.rateOfChange < 0)
                    return;

                console.log("line 74")
                
                item.direction = this.direction;
                item.rateOfChange = this.rateOfChange / 100;
            }

            
            this.items.push(item);
            this.name = "";
            this.value = null;
            this.direction = 1;
            this.rateOfChange = 1;
            this.$refs.nameinput.focus();
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

.inputs {
    @apply h-[38px] bg-gray-100 rounded outline-none px-4 invalid:outline-2 invalid:outline-red-400 focus:outline-2 focus:outline-blue-400;
}
</style>