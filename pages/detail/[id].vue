<script lang="ts" setup>
import { products } from '~/commons/data';

const route = useRoute()
const paramsId = route.params.id

const productById = products.filter(item => item.id === Number(paramsId))
</script>

<template>
  <div class="flex flex-col md:flex-row items-start gap-4">
    <img 
      class="rounded-lg"
      :src="productById[0].image" 
      alt="gambar produk"
    >
    <div class="flex flex-col gap-2">
      <h1 class="text-2xl">{{ productById[0].title }}</h1>
      <p class="text-lg">Harga: {{ productById[0].price }}</p>
      <p class="text-lg">Stok Barang: {{ productById[0].stock }}</p>
      <p class="text-lg">{{ productById[0].description }}</p>

      <div class="flex flex-row gap-2">
        <button class="min-w-[120px] bg-blue-500 text-white p-2 rounded-lg">
          Tambah Keranjang
        </button>
        <button class="min-w-[120px] border-2 border-blue-500 text-blue-500 p-2 rounded-lg">
          Beli
        </button>
      </div>
    </div>
  </div>
</template>