<script setup>
import { ref } from 'vue'
const pages = ref(10)
const activePage = ref(4)

const prevPage = () => 
{
    if (activePage.value > 1)
    {
        activePage.value--
    }
}

const nextPage = () => 
{
    if (activePage.value < pages.value)
    {
        activePage.value++
    }
}
</script>

<template>    
    <div class="pagination">
        <button class="action" :disabled="activePage === 1" @click="prevPage">Prev</button>
        <button class="page" v-for="page in pages" :key="page" :class="page === activePage ? 'active' : ''" @click="activePage = page">
            {{ page }}
        </button> 
        <button class="action" :disabled="activePage === pages" @click="nextPage">Next</button>
    </div>
</template>

<style lang="postcss" scoped>
  .pagination {
    @apply flex justify-center gap-4 bg-black;
    .action {
      @apply rounded-md p-2 font-medium text-white hover:bg-white hover:text-black disabled:text-slate-400 hover:disabled:bg-black my-5 transition-all;
    }
    .page {
      @apply rounded-md p-2 font-medium text-white  hover:bg-white hover:text-black transition-all my-5;
      &.active {
        @apply bg-white text-black;
      }
    }
  }
</style>