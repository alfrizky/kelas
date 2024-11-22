<script lang="ts" setup>
import { products } from '~/commons/data';

const productById = products
</script>

<template>
  <div class="flex flex-col gap-4">
    <h1 class="text-2xl font-medium">Keranjang</h1>
    <div class="flex flex-col md:flex-row justify-between items-start">
      <div class="flex flex-col gap-2">
        <div class="flex flex-col md:flex-row items-start gap-4">
          <img 
            :src="productById[0].image" 
            alt="gambar produk"
            width="150"
            height="150"
          >
          <div class="flex flex-col gap-2">
            <h1 class="text-xl">{{ productById[0].title }}</h1>
            <p class="text-lg">{{ productById[0].price }}</p>

            <label for="qty">Jumlah</label>
            <input 
              name="qty" 
              class="border-2 border-slate-400 rounded-lg p-2" 
              type="number"
            />

            <button class="w-fit border-2 text-sm border-blue-500 text-blue-500 p-2 rounded-lg">
              Hapus Barang
            </button>
          </div>

        </div>
      </div>
      <div class="flex flex-col gap-4">
        <h1 class="text-2xl font-medium">Ringkasan Belanja</h1>
        <div class="flex flex-row justify-between items-center">
          <p class="text-md">Total</p>
          <p class="text-md">Rp49.000</p>
        </div>

        <hr>

        <button class="min-w-[120px] text-lg bg-blue-500 text-white p-2 rounded-lg">
          Beli
        </button>
      </div>
    </div>
  </div>
</template>