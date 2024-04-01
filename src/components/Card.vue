<script setup>
defineProps({
  imageUrl: String,
});
</script>

<template>
  <div
    class="relative border border-slate-100 rounded-3xl w-60 p-8 cursor-pointer m-10 hover:-translate-y-2 hover:shadow-xl transition bg-white"
  >
    <img src="/unliked.svg" alt="Like" class="absolute top-10 left-10" />
    <img :src="imageUrl" alt="sneakers" />

    <p class="mt-2">Мужские Кроссовки Nike Blazer Mid Suede</p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цeна:</span>
        <span>12 999 руб.</span>
      </div>
      <img src="/plus.svg" alt="Add" />
    </div>
  </div>
</template>
