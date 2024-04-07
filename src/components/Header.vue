<script setup>
defineProps({
  totalPrice: Number,
});
const emit = defineEmits(["openDrawer"]);
</script>

<template>
  <header class="flex justify-between border-b border-slate-200 px-10 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="Logo" class="w-10" />

      <div>
        <h2 class="text-xl font-bold uppercase">Vue</h2>
        <p class="text-slate-400">
          A progressive, incrementally-adoptable JavaScript framework
        </p>
      </div>
    </div>
    <ul class="flex items-center gap-10">
      <li
        @click="emit('openDrawer')"
        class="flex items-center cursor-pointer gap-3 text-slate-500 font-bold hover:text-black"
      >
        <img src="/cart.svg" alt="Cart" />
        <span>{{ totalPrice }} руб.</span>
      </li>
      <li
        class="flex items-center cursor-pointer gap-3 text-slate-500 font-bold hover:text-black"
      >
        <img src="/heart.svg" alt="Cart" />
        <span>Закладки</span>
      </li>
      <li
        class="flex items-center cursor-pointer gap-3 text-slate-500 font-bold hover:text-black"
      >
        <img src="/user.svg" alt="Cart" />
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>
