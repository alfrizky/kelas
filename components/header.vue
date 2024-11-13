<template>
  <header class="flex flex-row justify-between items-center px-6 md:px-12 py-3 bg-slate-500 text-white">
    <div>NuxtCommerce</div>
    <ul class="flex flex-row items-center gap-4">
      <li>
        <NuxtLink to="/">
          Home
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/cart">
          Keranjang
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/dashboard">
          Dashboard
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/dashboard/transaction">
          Transaksi
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/profile">
          Profile
        </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/login">
          Login
        </NuxtLink>
      </li>
    </ul>
  </header>
</template>