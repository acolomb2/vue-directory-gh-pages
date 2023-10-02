<script setup>
import { ref } from 'vue'
const brand = ref(' Click to generate more')
</script>

<template>
    <nav>
        <div class="wrapper">
            <div class="brand">
                <span class="brand-title"><a href="index.html" > {{ brand }}</a></span>
            </div>
            <div class="menu">
                <a href="logout.html" class="menu-login">Logout</a>
            </div>
        </div>
    </nav>
</template>

<style scoped lang="postcss">
    nav{
        @apply flex h-20 bg-black text-white;

        .wrapper{
            @apply container mx-auto flex w-full items-center justify-between;
            .brand{
                &-title{
                    @apply text-2xl font-bold text-white;
                }
            }

            .menu{
                @apply flex gap-2;
                &-item{
                    @apply rounded-md px-4 py-2 hover:bg-yellow-500 hover:text-slate-900;
                }
                &-login{
                    @apply rounded-md px-4 py-2 bg-red-500 hover:bg-red-700 text-red-100;
                }
            }
        }
    }

    
</style>