<template>
  <div>
    {{ products }}
    <ul>
      <li v-for="product in products" :key="product.id">
        <img :src="product.imageUrl" :alt="product.name" />
        <p>{{ product.name }}</p>
        <p>{{ product.price }}</p>
      </li>
    </ul>
  </div>
</template>

<script setup>
// const { data, error, pending, refresh } = await useFetch(
//   "http://localhost:3000/products"
// );

// const {
//   data: products,
//   pending,
//   error,
//   refresh,
// } = await useFetch("http://localhost:3000/products", {
//   onRequest({ request, options }) {
//     // Set the request headers
//   },
//   onRequestError({ request, options, error }) {
//     // Handle the request errors
//   },
//   onResponse({ request, response, options }) {
//     // Process the response data
//   },
//   onResponseError({ request, response, options }) {
//     // Handle the response errors
//   },
// });

const {
  data: products,
  pending,
  error,
  refresh,
} = await useAsyncData("products", () =>
  $fetch("http://localhost:3000/products")
);
</script>
