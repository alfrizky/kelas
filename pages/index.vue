<script lang="ts" setup>
import { products } from '~/commons/data';

</script>

<template>
  <div class="flex flex-col gap-4">
    <h1 class="text-lg font-semibold">Daftar Barang</h1>

    <ul class="flex flex-row flex-wrap gap-2">
      <li 
        class="p-2 rounded-md w-[150px] h-auto shadow-lg transition-transform transform hover:scale-105" 
        v-for="(product, index) in products"
        :key="index"
      >
        <NuxtLink :to="`detail/${product.id}`">
          <div class="flex flex-col gap-1">
            <img 
              :src="product.image" 
              alt="gambar produk"
            />
            <h3 class="text-xs">{{ product.title }}</h3>
            <h3 class="text-xs font-bold">{{ product.price }}</h3>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>