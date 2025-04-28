<script setup lang="ts">
import { ref, reactive } from 'vue'
import { useRouter } from 'vue-router'

const form = reactive({
  identifier: '',
  password: '',
})

const router = useRouter()
const handleSubmit = async () => {
  console.log(form)
  try {
    const res = await fetch('http://localhost:1337/api/auth/local', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(form),
    })
    const data = await res.json()
    console.log(data)
    router.push('/profil')
  } catch (error) {
    console.log(error)
  }
}
</script>

<template>
  <TitlePage title="Login" />
  <form @submit.prevent="handleSubmit">
    <input type="text" placeholder="Email" v-model="form.identifier" />
    <input type="password" placeholder="Password" v-model="form.password" />
    <button type="submit">Login</button>
  </form>
</template>

<style scoped>
input {
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}
</style>
