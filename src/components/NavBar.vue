<script setup>
import { ref } from 'vue'
import { useAuth } from '@/composables/useAuth'
const { isAuthenticated, logout, user } = useAuth()
const brand = ref('Squares Space')

</script>

<template>
    <nav>
        <div class="wrapper">
            <RouterLink :to="{ name: 'Home' }" class="brand">
                <span class="brand-title">{{ brand }}</span>
            </RouterLink>
            <div class="menu">
                <p v-show="isAuthenticated" class="px-2 py-4">Welcome back
                    <strong><i>{{ user.name }}</i></strong>
                </p>
                <div v-if="isAuthenticated">
                    <RouterLink :to="{ name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>
                    <button class="menu-logout" @click="logout">Logout</button>
                </div>
                <div v-else>
                    <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped lang="postcss">
    nav{
        @apply flex h-20 bg-black text-slate-200;

        .wrapper{
            @apply container ml-5 mx-auto flex w-full items-center justify-between;
            .brand{
                &-title{
                    @apply text-2xl font-bold text-white;
                }
            }

            .menu{
                @apply flex gap-2;
                & div {
                    @apply py-2;
                }
                &-item{
                    @apply rounded-sm px-4 py-2 hover:bg-white hover:text-black transition-all mr-4;
                }
                &-login{
                    @apply border-2 mr-5 rounded-sm bg-black px-4 py-2 text-white hover:bg-white hover:text-black transition-all;
                }
                &-logout {
                    @apply border-2 mr-5 rounded-sm bg-black px-4 py-2 text-white hover:bg-red-500 transition-all;
                }
            }
        }
    }

    
</style>