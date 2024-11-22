<script lang="ts" setup>
const client = useSupabaseClient()
const router = useRouter()

const onClickCancel = () => {
  console.log("Pindah ke halaman sebelumnya");

  router.back()
}

const title = ref('')
const description = ref('')
const price = ref(0)
const stock = ref(0)
const image = ref('')

const onSubmit = async () => {
  const { data: products }: { data: any } = await useAsyncData('product', async () => {
    const { data, error }: { data: any, error: any} = await client
      .from('product')
      .insert(
        {
          "title": title.value,
          "description": description.value,
          "price": price.value,
          "stock": stock.value,
          "image": image.value
        }
      )
      .select()

      return data
  })

  if (products) {
    onClickCancel()
  }
}

</script>

<template>
  <div class="flex flex-col gap-4">
    <h1 class="text-2xl font-semibold">
      Tambah Barang
    </h1>

    <form action="#">
      <div class="flex flex-col gap-2">
        <div class="w-full flex flex-col gap-1">
          <label for="title">Judul barang</label>
          <input
            name="title"
            class="p-2 border-2 border-slate-400 rounded-md" 
            placeholder="Judul barang" 
            type="text"
            v-model="title"
          >
        </div>
        
        <div class="w-full flex flex-col gap-1">
          <label for="desc">Deskripsi barang</label>
          <textarea
            name="desc"
            class="p-2 border-2 border-slate-400 rounded-md" 
            placeholder="Deskripsi barang" 
            type="text"
            v-model="description"
          ></textarea>
        </div>

        <div class="flex flex-row gap-2 items-center w-full">
          <div class="w-full flex flex-col gap-1">
            <label for="price">Harga barang (Rp)</label>
            <input
              name="price"
              class="w-full p-2 border-2 border-slate-400 rounded-md" 
              placeholder="Harga barang" 
              type="number"
              v-model="price"
            >
          </div>
          
          <div class="w-full flex flex-col gap-1">
            <label for="stock">Stok Barang</label>
            <input
              name="stock"
              class="w-full p-2 border-2 border-slate-400 rounded-md" 
              placeholder="Stok barang" 
              type="number"
              v-model="stock"
            >
          </div>
        </div>

        <div class="flex flex-col gap-1">
          <label for="image">Gambar Barang</label>
          <input
            name="image"
            class="p-2 border-2 border-slate-400 rounded-md" 
            placeholder="Url gambar barang" 
            type="text"
            v-model="image"
          >
        </div>

        <div class="flex flex-row gap-2 items-center">
          <button 
            type="button" 
            class="w-fit border-2 border-blue-500 text-blue-500 p-2 rounded-lg px-4" 
            @click="onClickCancel"
          >
            Batal
          </button>
          <button 
            type="button" 
            class="w-fit bg-blue-500 text-white p-2 rounded-lg px-4"
            @click="onSubmit"
          >
            Simpan Barang
          </button>
        </div>

      </div>
    </form>
  </div>
</template>