<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import CardList from "../components/CardList.vue";

const favorites = ref([]);

onMounted(async () => {
  try {
    const { data } = await axios.get(
      "https://78345423b3c66473.mokky.dev/favorites?_relations=items"
    );
    favorites.value = data.map((obj) => obj.item);
  } catch (err) {
    console.log(err);
  }
});
</script>

<template>
  <div>
    <h2 class="text-3xl font-bold mb-8">Мои закладки</h2>
    <CardList :items="favorites" is-favorites />
  </div>
</template>
