<script setup>
import Card from "./Card.vue";

const onClickAdd = () => {
  alert("Добавлено");
};
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      imageUrl="/sneakers/1.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
      :price="12999"
      :isAdded="false"
      :isFavorite="true"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
