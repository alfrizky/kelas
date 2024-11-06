<script lang="ts" setup>
import { products } from '~/commons/data';

const router = useRouter()

const onClickCreateProduct = () => {
    console.log("Pindah ke dashboard/create");

    router.push('/dashboard/create')
}
</script>
<template>
    <div class="flex flex-col gap-4">
        <div class="flex flex-row justify-between">
            <h1 class="text-2xl font-semibold">List Barang</h1>
            <button class="min-w[120px] bg-blue-500 text-white p-2 rounded-"
            v-on:click="onClickCreateProduct"
            >
                Tambah Barang
            </button>
        </div>
    <table class="w-full border-">
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
            v-for="(product, index) in products"
            :key="index"
            >
            <th scope="row" clas="px-6 py-4 font-medium text-left">
                {{ product.title }}
            </th>
            <td class="px-6 py-4 text-left">
                {{ product.price }}
            </td>
            <td class="px-6 py-4 text-left">
                {{ product.stock }}
            </td>
            <td class="px-6py-4text-left">
                <NuxtLink :to="`/dashboard/edit/${product.id}`" class="text-blue-500">
                    Edit
                </NuxtLink>
            </td>
            </tr>
        </tbody>
    </table>
</div>
</template>