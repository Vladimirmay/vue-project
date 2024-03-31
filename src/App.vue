<script setup>
import Header from "./components/Header.vue";
import { ref } from "vue";
const count = ref(0);
</script>

<template>
  <div class="bg-white w-4/5 m-auto h-screen rounded-xl drop-shadow-xl mt-14">
    <Header />

    <div>
      <div>
        <img src="/unliked.svg" alt="Like" />
        <img src="/sneakers/1.jpg" alt="sneakers" />
        <p>Мужские Кроссовки Nike Blazer Mid Suede</p>
        <div class="flex justify-between">
          <div>
            <span>Цeна:</span>
            <span>12 999 руб.</span>
          </div>
          <img src="/plus.svg" alt="Add" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
