<script setup>
  import { ref } from 'vue'
  import { useRouter, useRoute } from 'vue-router'
  import { useAuth } from '@/composables/useAuth'
  const { login, logout } = useAuth()
  const router = useRouter()
  const route = useRoute()
  const username = ref('')
  const password = ref('')
  const logUserIn = () => {
    if (login(username.value, password.value)) {
      if (route.query.redirect) {
        router.push(route.query.redirect)
      } else {
        router.push({ name: 'Home' })
      }
    } else {
      logout()
    }
  }
</script>

<template>
  <div class="loginLayout">
    <div><h1 class="motto font-bold">OOPS! All Squares</h1></div>
  <div>
    <form class="login-form" @submit.prevent="logUserIn">
    <input v-model="username" type="text" placeholder="Username" />
    <input v-model="password" type="password" placeholder="Password" />
    <button type="submit" class="bg-white px-4 py-2 border-2 ml-auto rounded-sm hover:bg-green-400 transition-all flex-col">
      <div>Log In</div>
      <div class="hidden"><img src="loading-43.png" alt="loading icon" width="15" height="15"></div>
    </button>
  </form>
  </div>
  </div>
</template>

<style scoped lang="postcss">
  .login-form {
    @apply mr-5 ml-auto mt-10 flex max-w-md flex-col gap-4 rounded-md bg-white p-8 shadow-lg;
    & input {
      @apply rounded-sm px-4 py-2 text-xl ring-1 ring-slate-300;
    }
  }

img{
  animation-name: spin;
  animation-duration: 1000ms;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

@keyframes spin {
    from {
        transform:rotate(0deg);
    }
    to {
        transform:rotate(360deg);
    }
}

.motto
{
  font-size: 4em;
  margin-left: .5em;
  width: 100%;
}

.loginLayout
{
  display:flex;
  font-family: Trebuchet MS;
  justify-content: space-between;
  

}
</style>