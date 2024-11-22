<script lang="ts" setup>
const client = useSupabaseClient()

const { data: products }: { data: any } = await useAsyncData('product', async () => {
  const { data } = await client.from('product').select().order('created_at', { ascending: true })

  return data
})
</script>

<template>
  <div class="flex flex-col gap-4">
    <h1 class="text-2xl font-semibold">Daftar Barang</h1>

    <ul class="flex flex-row flex-wrap gap-4">
      <li 
        class="p-2 rounded-md w-[250px] h-auto shadow-lg transition-transform transform hover:scale-105" 
        v-for="(product, index) in products"
        :key="index"
      >
        <NuxtLink :to="`detail/${product.id}`">
          <div class="flex flex-col gap-1">
            <img 
              :src="product.image" 
              alt="gambar produk"
            />
            <h3 class="text-lg line-clamp-2">{{ product.title }}</h3>
            <h3 class="text-lg font-bold">Rp{{ product.price }}</h3>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>