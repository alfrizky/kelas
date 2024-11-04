<template>
    <header class="flex flex-row justify-between items-center px-6 md:px-12 py-3 bg-slate-500 text-white">
      <div>Logo</div>
      <ul class="flex flex-row items-center gap-4">
        <li>
          <NuxtLink 
            to="/" 
            class="hover:text-yellow-300 hover:text-lg transition-all"
          >
            Home
          </NuxtLink>
        </li>
        <li>
          <NuxtLink 
            to="/about" 
            class="hover:text-yellow-300 hover:text-lg transition-all"
          >
            About
          </NuxtLink>
        </li>
        <li>
          <NuxtLink 
            to="/profile" 
            class="hover:text-yellow-300 hover:text-lg transition-all"
          >
            Profile
          </NuxtLink>
        </li>
        <li>
          <NuxtLink 
            to="/cart" 
            class="hover:text-yellow-300 hover:text-lg transition-all"
          >
            Keranjang
          </NuxtLink>
        </li>
      </ul>
    </header>
  </template>
  