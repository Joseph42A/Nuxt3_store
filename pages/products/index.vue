<template>
  <div>
    <!-- <h1>Products</h1> -->
    <div class="grid grid-cols-4 gap-5">
      <div v-for="product in products" :key="product.id">
        <ProductCard :product="product" />
      </div>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: "products",
});

const {
  data: { _rawValue: products },
} = await useFetch("https://fakestoreapi.com/products");

useHead({
  title: "Merch",
  meta: [{ name: "description", content: "Merch in Joso store" }],
});
</script>

<style scoped></style>
