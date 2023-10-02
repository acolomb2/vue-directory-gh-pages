<template>
    <form class="newThingInput">
    <input id="newThing" type="text" placeholder="Use CTRL + F to search" class="search"/>
    </form>
</template>

<script>
const newInput = document.getElementById('newThing');
console.log(newInput);
</script>

<style scoped lang="postcss">
    .wrapper{
        @apply relative flex w-full items-stretch;
        .search{
            @apply px-8 py-4 placeholder-slate-400 text-slate-700 rounded-md border-0 outline-none focus:ring focus:ring-yellow-500;
        }
        .icon{
            @apply absolute right-0 pr-8 py-4 z-10 text-slate-400;
        }
    }
</style>