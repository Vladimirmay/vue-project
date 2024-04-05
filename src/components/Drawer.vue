<script setup>
import DrawerHead from "./DrawerHead.vue";
import CartItem from "./CartItem.vue";
</script>

<template>
  <div>
    <div
      class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70"
    ></div>
    <div class="bg-white w-96 h-full fixed right-0 z-20 top-0 p-8">
      <DrawerHead />
      <CartItem />
      <CartItem />
      <CartItem />
      <CartItem />
    </div>
  </div>
</template>
