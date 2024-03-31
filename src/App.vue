<script setup>
import Header from "./components/Header.vue";
import { ref } from "vue";
const count = ref(0);
</script>

<template>
  <div class="bg-white w-4/5 m-auto h-screen rounded-xl drop-shadow-xl mt-14">
    <Header />
  </div>
</template>

<style scoped></style>
