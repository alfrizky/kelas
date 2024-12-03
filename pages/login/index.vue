<script setup lang="ts">
const client = useSupabaseClient()

const email = ref('')
const password = ref('')
const errorMsg = ref('')

const onClickLogin = async () => {
  try {
    const { data, error: error_login } = await client.auth.signInWithPassword({
      email: email.value,
      password: password.value
    })
  
    if (data.user) {
      navigateTo('profile')
    }
  
    if (error_login) {
      errorMsg.value = error_login.message
    }
  } catch (error: any) {
    alert(error.error_description || error.message)
  }

}

</script>

<template>
  <div class="w-full">
    <div class="flex flex-col gap-4 w-[480px] mx-auto p-8  shadow-xl rounded-lg">
      <h1 class="text-2xl font-semibold text-center" >Login to NuxtCommerce</h1>

      <form @submit.prevent="onClickLogin">
        <div class="flex flex-col gap-2">
          <div class="flex flex-col gap-1">
            <label for="email">Email</label>
            <input 
              name="email" 
              type="email" 
              class="w-full border-2 border-slate-600 p-2 rounded-lg"
              v-model="email"
            >
          </div>

          <div class="flex flex-col gap-1">
            <label for="password">Password</label>
            <input 
              name="password" 
              type="password"
              class="w-full border-2 border-slate-600 p-2 rounded-lg"
              v-model="password"
            >
          </div>
          
          <button class="min-w-[120px] text-lg bg-blue-500 text-white p-2 rounded-lg">
            Login
          </button>

          <p v-if="errorMsg" class="text-red-500">
            {{ errorMsg }}
          </p>

          <div class="text-md text-center mt-2">
            Belum punya akun? 
            <NuxtLink 
              class="text-blue-500 font-semibold" 
              to="/register"
            >
              Daftar Sekarang
            </NuxtLink> 
          </div>
        </div>
      </form>
    </div>
    
  </div>
</template>