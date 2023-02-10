<script setup>
import { ref } from "vue";
import axios from "axios";
/* const data = ref([]);
axios
  .get("https://fakestoreapi.com/products")
  .then((res) => data.value = res.data);

console.log(data.value); */

const data = ref([]);
const config = {
  method: "get",
  url: "https://fakestoreapi.com/products",
  headers: {},
};
axios(config)
  .then(function (response) {
    data.value = response.data;
    console.log(response.data);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>

<template>
  <h3>Store</h3>
  <table>
    <tr>
      <th></th>
    </tr>
    <tr v-for="product in data" :key="product.id">
      <td>{{ product.title }}</td>
      <td><img :src="product.image" alt="asx" style="height: 100px;"></td>
    </tr>
  </table>
</template>

<style scoped></style>
