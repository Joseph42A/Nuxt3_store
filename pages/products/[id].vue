<template>
  <div>
    <Head>
      <Title>Joso {{ product.title }}</Title>
      <Meta name="description" :content="product.description" />
    </Head>
    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
definePageMeta({
  layout: "products",
});
const { id } = useRoute().params;
const uri = `https://fakestoreapi.com/products/${id}`;

const {
  data: { _rawValue: product },
} = await useFetch(uri, { key: id });

if (!product?.id) {
  throw createError({
    status: 404,
    statusMessage: "Product Not Found!",
    fatal: true,
  });
}
</script>

<style scoped></style>
