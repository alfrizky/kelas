<script setup lang="ts">

const client = useSupabaseClient()
const router = useRouter()

const transactions = ref([]) 

const onClickCreateTransaction = () => {
  router.push('/dashboard/transaction/create')
}

onMounted(async () => {
  try {
    const { data } = await client.from('transaction_user')
      .select(`
        id,
        user,
        total_price,
        created_at,
        transaction (
          product (*),
          total_price,
          qty_product
        )
      `)
      .order('created_at', { ascending: true })
      
    return transactions.value = data
  } catch (error) {
    alert(`Failed to fetch transaction: ${error}`)
    console.error('Failed to fetch transaction', error)
  }
})
</script>

<template>
  <div class="flex flex-col gap-4">
    <div class="flex flex-row justify-between">
      <h1 class="text-2xl font-semibold">List Transaksi</h1>
      <button 
        class="min-w-[120px] bg-blue-500 text-white p-2 rounded-lg" 
        v-on:click="onClickCreateTransaction"
      >
        Tambah Transaksi
      </button>
    </div>

    <table class="w-full border-2">
      <thead class="border-b-2">
        <tr>
          <th scope="col" class="text-left px-6 py-3">
            Id Transaksi
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Daftar Belanja
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Total Harga
          </th>
          <th scope="col" class="text-left px-6 py-3">
            Action
          </th>
        </tr>
      </thead>
      <tbody>
        <tr class="border-b-2" v-for="(item, idx) in transactions" :key="idx">
          <th scope="row" class="px-6 py-4 font-medium text-left">
            Transaksi {{ item.id }}
          </th>
          <td class="px-6 py-4 text-left">
            <ul v-for="(product, index) in item.transaction" :key="index">
              <li>{{ product.product.title }} x {{ product.qty_product }} = {{ product.total_price }}</li>
            </ul>
          </td>
          <td class="px-6 py-4 text-left">
            Rp{{ item.total_price }}
          </td>
          <td class="px-6 py-4 text-left">
            <NuxtLink to="/dashboard/transaction/edit/1" class="text-blue-500">
              Edit
            </NuxtLink>
          </td>
        </tr>
      </tbody>
    </table>
  </div>


</template>