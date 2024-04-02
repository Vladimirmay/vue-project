<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
});
</script>

<template>
  <div
    class="relative border border-slate-100 rounded-3xl w-60 p-8 cursor-pointer m-10 hover:-translate-y-2 hover:shadow-xl transition bg-white"
  >
    <img
      @click="onClickFavorite"
      :src="isFavorite ? '/liked.svg' : '/unliked.svg'"
      alt="Like"
      class="absolute top-10 left-10"
    />
    <img :src="imageUrl" alt="sneakers" />

    <p class="mt-2">{{ title }}</p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цeна:</span>
        <span>{{ price }} руб.</span>
      </div>
      <img
        @click="onClickAdd"
        :src="!isAdded ? '/plus.svg' : '/btn-checked.svg'"
        alt="Add"
      />
    </div>
  </div>
</template>
