<template>
    <div class="flex flex-col gap-4">
        <h1 class="text-2xl font-semibold">
            Tambah Barang
        </h1>

        <form action="#">
            <div class="flex flex-col gap">
                <input type="text" class="p-2 border-2 border-slate-400 rounded-md"
                placeholder="Judul Barang">


                <textarea type="text" class="p-2 border-2 border-slate-400 rounded-md"
                placeholder="Deskripsi Barang">
                </textarea>

                <div class="flex flex-row gap-2 items-center w-full">
                    <input type="number" class="w-full p-2 border-2 border-slate-400 rounded-md"
                    placeholder="Harga Barang">

                    <input type="number" class="w-full p-2 border-2 border-slate-400 rounded-md"
                    placeholder="Stok Barang">
                </div>
            <div class="flex flex-col gap-1">
                <label for="image">Gambar Barang</label>
                <input type="file" class="p-2 border-2 border-slate-400 rounded-md"
                placeholder="Gambar Barang">
            </div>

                <div class="flex flex-row gap-2 items-center">
                    <button class="w-fit border-2 border-blue-500 text-blue-500 p-2 rounded-lg px-">
                        Batal
                    </button>
                    <button class="w-fit bg-blue-500 text-white p-2 rounded-lg px-4">
                        Simpan Barang
                    </button>
                </div>

            </div>
        </form>
    </div>
</template>