<script setup lang="ts">
const client = useSupabaseClient()
const user = useSupabaseUser()

const errorMsg = ref('')
const name = ref('')
const email = ref('')

if (user.value){
 const { data } = await client
 .from('profiles')
 .select('name')
 .eq('id', user.value.id)
 .single()

 if (data) {
  name.value = data.name
  email.value = user.value.email || ''
 }
}

const signOut = async () => {
  try{
    const title = 'Are you sure you want to logout?'
    if (confirm(title)) {
      const { error } = await client.auth.signOut()
      if (error) {
        return errorMsg.value = error.message
      }

      user.value = null
      navigateTo('login')
    }
  }catch (error: any) {
    alert(error.massage)

    console.log(error)
  }
}
</script>

<template>
  <div class="w-full">
    <div class="flex flex-col w-[480px] shadow-lg rounded-lg p-6 mx-auto gap-4">
      <div class="flex flex-col gap-1">
        <h1 class="text-2xl font-semibold">
         Hello, {{ name }}
        </h1>
        <span class="text-lg">{{ email }}</span>
      </div>

      <button class="min-w-[120px] text-lg bg-blue-500 text-white p-2 rounded-lg" @click="signOut">
        Logout
      </button>
    </div>
  </div>
</template>