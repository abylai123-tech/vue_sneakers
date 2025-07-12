<script setup>
import { ref, provide, watch, computed } from "vue";
import axios from "axios";

import DrawerHead from './DrawerHead.vue';
import CartItemList from './CartItemList.vue';
import InfoBlock from './InfoBlock.vue';

const emit = defineEmits(['createOrder'])

defineProps({
    totalPrice: Number,
    vatPrice: Number,
    buttonDisabled: Boolean
})

const {cart, closeDrawer} = provide('cart')

const  isCreatingOrder = ref(false);

const createOrder = async() => {
  try {
    isCreatingOrder.value = true;
     const { data } = await axios.post(`https://6c2b072e91f77630.mokky.dev/orders`, {
        items: cart.value,
        totalPrice: totalPrice.value
     })

     cart.value = []

     return data
  } catch (err) {
    console.log(err)
  } finally {
    isCreatingOrder.value = false;
  }
}

const cartButtonDisabled = computed(() => isCreatingOrder.value || cartIsEmpty);
</script>

<template>
    <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
    <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
        <DrawerHead />

        <div v-if="!totalPrice" class="flex h-full items-center">
           <InfoBlock title="Корзина пустая" description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ." image-url="/package-icon.png"/>            
        </div>

        <div v-else>
        <CartItemList />

            <div class="flex flex-col gap-4 mt-7">
                <div class="flex gap-2">
                    <span>Итого:</span>
                    <div class="flex-1 border-b border-dashed"></div>
                    <b>{{ totalPrice }} ₽</b>
                </div>

                    <div class="flex gap-2">
                    <span>Налог 5%:</span>
                    <div class="flex-1 border-b border-dashed"></div>
                    <b>{{ vatPrice }} ₽</b>
                </div>

                <button 
                :disabled="disabled"
                @click="() => emit('createOrder')"
                class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer"
                >
                    Оформить заказ
                </button>
            </div>
        </div>
    </div>
</template>