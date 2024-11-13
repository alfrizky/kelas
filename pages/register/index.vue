<template>
    <div class="w-full">
      <div class="flex flex-col gap-4 w-[480px] mx-auto p-8  shadow-xl rounded-lg">
        <h1 class="text-2xl font-semibold text-center">Register to NuxtCommerce</h1>
  
        <form action="#">
          <div class="flex flex-col gap-2">
            <div class="flex flex-col gap-1">
              <label for="name">Name</label>
              <input name="name" type="text" class="w-full border-2 border-slate-600 p-2 rounded-lg">
            </div>
  
            <div class="flex flex-col gap-1">
              <label for="email">Email</label>
              <input name="email" type="email" class="w-full border-2 border-slate-600 p-2 rounded-lg">
            </div>
  
            <div class="flex flex-col gap-1">
              <label for="password">Password</label>
              <input name="password" type="password" class="w-full border-2 border-slate-600 p-2 rounded-lg">
            </div>
            
            <button class="min-w-[120px] text-lg bg-blue-500 text-white p-2 rounded-lg">
              Register
            </button>
  
            <div class="text-md text-center mt-2">
              Sudah punya akun? 
              <NuxtLink 
                class="text-blue-500 font-semibold" 
                to="/login"
              >
                Login Sekarang
              </NuxtLink> 
            </div>
          </div>
        </form>
      </div>
      
    </div>
  </template>