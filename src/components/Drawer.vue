<script setup>
import { computed, inject, ref } from "vue";
import axios from "axios";
import DrawerHead from "./DrawerHead.vue";
import CartItemList from "./CartItemList.vue";
import InfoBlock from "./InfoBlock.vue";

const props = defineProps({
  totalPrice: Number,
  vatPrice: Number,
});

const { cart, closeDrawer } = inject("cart");
const isCreatingOrder = ref(false);
const orderId = ref(null);

const createOrder = async () => {
  try {
    isCreatingOrder.value = true;
    const { data } = await axios.post(
      "https://78345423b3c66473.mokky.dev/orders",
      {
        items: cart.value,
        totalPrice: props.totalPrice.value,
      }
    );

    cart.value = [];
    orderId.value = data.id;
    // return data;
  } catch (err) {
    console.log(err);
  } finally {
    isCreatingOrder.value = false;
  }
};
const cartIsEmpty = computed(() => cart.value.length === 0);
const cartButtonDisabled = computed(
  () => isCreatingOrder.value || cartIsEmpty.value
);
</script>

<template>
  <div>
    <div
      class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70"
    ></div>
    <div class="bg-white w-96 h-full fixed right-0 z-20 top-0 p-8">
      <DrawerHead />

      <div v-if="!totalPrice || orderId" class="flex h-full items-center">
        <InfoBlock
          v-if="!totalPrice && !orderId"
          title="Корзина пуста"
          description="Добавьте в корзину один или более позиций, чтобы оформить заказ."
          imageUrl="/empty-cart.jpg"
        />
        <InfoBlock
          v-if="orderId"
          title="Заказ оформлен!"
          :description="`Ваш заказ #${orderId} был оформлен. Мы свяжемся с вами в ближайшее время.`"
          imageUrl="/complete-order.jpg"
        />
      </div>

      <CartItemList v-if="totalPrice" />
      <div v-if="totalPrice" class="flex flex-col gap-4 mt-7">
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
          :disabled="cartButtonDisabled"
          @click="createOrder"
          class="mt-4 transition bg-lime-500 text-white disabled:bg-slate-300 rounded-3xl w-full py-4 mt-8 hover:bg-lime-600 active:hover:bg-lime-700 cursor-pointer"
        >
          Оформить заказ
        </button>
      </div>
    </div>
  </div>
</template>
