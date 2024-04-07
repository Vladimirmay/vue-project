<script setup>
const emit = defineEmits(["onClickRemove"]);

defineProps({
  id: Number,
  title: String,
  imageUrl: String,
  price: Number,
});
</script>

<template>
  <div class="border border-slate-200 rounded-3xl w-full p-6 mt-5">
    <div class="flex gap-5 relative">
      <img :src="imageUrl" :alt="title" class="w-20" />
      <div>
        <p class="text-sm">{{ title }}</p>
        <b>{{ price }}</b>
      </div>
      <img
        @click="emit('onClickRemove')"
        src="/btn-remove.svg"
        alt="delete"
        class="absolute bottom-0 right-0 cursor-pointer opacity-40 hover:opacity-100 transition"
      />
    </div>
  </div>
</template>
