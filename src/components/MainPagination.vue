<script setup>
import { ref } from 'vue'
const pages = ref(10)
const activePage = ref(localStorage.getItem("currentPage"))
activePage.value++
activePage.value--
console.log(activePage)
console.log(activePage.value)


const prevPage = () => 
{
    if (activePage.value > 1)
    {
        activePage.value--
      localStorage.setItem("currentPage", activePage.value)
    }
  window.location.reload()
}

const nextPage = () => 
{
    if (activePage.value < pages.value)
    {
      activePage.value++
      localStorage.setItem("currentPage", activePage.value)
        
  }
    
  window.location.reload()
}

const updatePage = () =>
{
  localStorage.setItem("currentPage", activePage.value)
  window.location.reload()
}

</script>

<template>    
    <div class="pagination">
        <button class="action" :disabled="activePage === 1" @click="prevPage">Prev</button>
        <button class="page" v-for="page in pages" :key="page" :class="page === activePage ? 'active' : ''" @click="activePage = page; updatePage()">
            {{ page }}
        </button> 
        <button class="action" :disabled="activePage === pages" @click="nextPage">Next</button>
    </div>
</template>

<style lang="postcss" scoped>
  .pagination {
    @apply flex justify-center gap-4 bg-black;
    .action {
      @apply rounded-sm bg-black p-2 font-medium text-white hover:text-black shadow-md transition-all  hover:bg-slate-200 disabled:text-slate-400 hover:disabled:bg-black m-3;
    }
    .page {
      @apply rounded-sm bg-black p-2 font-medium text-white shadow-md hover:bg-white hover:text-black transition-all m-3;
      &.active {
        @apply text-black bg-white;
      }
    }
  }
</style>