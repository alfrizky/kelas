<script setup lang="ts">
const client = useSupabaseClient()
const router = useRouter()

const listProducts = ref<any>([])

const getProduct = async () => {
  const { data: products }: { data: any } = await useAsyncData('product', async () => {
    const { data } = await client.from('product').select().order('created_at', { ascending: true })
  
    return data
  })
  
  listProducts.value = products.value
}

const onClickCreateProduct = () => {
  console.log("Pindah ke dashboard/create");

  router.push('/dashboard/create')
}

const onClickDeleteProduct = async (id: number) => {
  let title = 'Are you sure you want to delete this product?'
  
  if (confirm(title)) {
    const { data: deletedProduct }: { data: any } = await useAsyncData('product', async () => {
      const { data } = await client.from('product').delete().eq('id', id)

      return data
    })

    if (deletedProduct) {
      await getProduct()
    }
    
  } {
    console.log('No');
  }
}

onMounted(async () => {
  await nextTick()
  await getProduct()
})
</script>

<template>
  <div class="flex flex-col gap-4">
    <div class="flex flex-row justify-between">
      <h1 class="text-2xl font-semibold">List Barang</h1>
      <button 
        class="min-w-[120px] bg-blue-500 text-white p-2 rounded-lg" 
        v-on:click="onClickCreateProduct"
      >
        Tambah Barang
      </button>
    </div>

    <table class="w-full border-2">
      <thead class="border-b-2">
        <tr>
          <th scope="col" class="text-left px-6 py-3">
            Nama Produk
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Harga
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Jumlah Stok
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Action
          </th>
        </tr>
      </thead>
      <tbody>
        <tr 
          class="border-b-2"
          v-for="(product, index) in listProducts"
          :key="index"
        >
          <th scope="row" class="px-6 py-4 font-medium text-left">
            {{ product.title }}
          </th>
          <td class="px-6 py-4 text-left">
            Rp{{ product.price }}
          </td>
          <td class="px-6 py-4 text-left">
            {{ product.stock }}
          </td>
          <td class="px-6 py-4 text-left">
            <NuxtLink :to="`/dashboard/edit/${product.id}`" class="text-blue-500">
              Edit
            </NuxtLink>

            <div class="text-red-500 cursor-pointer" @click="onClickDeleteProduct(product.id)">
              Delete
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>


</template>