<template>
  <div class="app">
    <div><input type="text" /></div>
    <ul class="product-list">
      <li
        v-for="product in products"
        :key="product.id"
        @click="moveToDetail(product.id)"
      >
        <img
          :src="product.imageUrl + '?ranfom=' + product.id"
          :alt="product.name"
          class="product-image"
        />
        <p class="product-name">{{ product.name }}</p>
        <span class="product-price">{{ product.price }}</span>
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

// [TODO: 이미지에 랜덤 숫자 넣어서 반환하기]
// const response = 값
// const products = response.data.map((item) => ({
//     ...item,
//     imageUrl = `${item.imageUrl}?random=${Math.random()}`
// }))
// return products

const moveToDetail = (id) => {
  console.log(id);
};
</script>

<style scoped>
.cart-wrapper {
  position: sticky;
  float: right;
  bottom: 50px;
  right: 50px;
}
.cart-wrapper .btn {
  display: inline-block;
  height: 40px;
  font-size: 1rem;
  font-weight: 500;
}
</style>

<style lang="scss" scoped>
.product-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 16px;
  list-style: none;

  .product-image {
    display: block;
    width: 400px;
    height: 250px;
  }

  .product-name {
    margin: 8px 0 4px;
    font-size: 18px;
    font-weight: bold;
  }
}
</style>
