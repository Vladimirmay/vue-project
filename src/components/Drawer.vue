<script setup>
import DrawerHead from "./DrawerHead.vue";
import CartItemList from "./CartItemList.vue";

const emit = defineEmits(["createOrder"]);
defineProps({
  totalPrice: Number,
  vatPrice: Number,
  buttonDisabled: Boolean,
});
</script>

<template>
  <div>
    <div
      class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70"
    ></div>
    <div class="bg-white w-96 h-full fixed right-0 z-20 top-0 p-8">
      <DrawerHead />
      <CartItemList />
      <div class="flex flex-col gap-4 mt-7">
        <div class="flex gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ totalPrice }} руб.</b>
        </div>
        <div class="flex gap-2">
          <span>Налог 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ vatPrice }} руб.</b>
        </div>
        <button
          :disabled="buttonDisabled"
          @click="() => emit('createOrder')"
          class="mt-4 transition bg-lime-500 text-white disabled:bg-slate-300 rounded-3xl w-full py-4 mt-8 hover:bg-lime-600 active:hover:bg-lime-700 cursor-pointer"
        >
          Оформить заказ
        </button>
      </div>
    </div>
  </div>
</template>
