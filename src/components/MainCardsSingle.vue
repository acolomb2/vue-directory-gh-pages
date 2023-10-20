<script setup>
import { faker } from '@faker-js/faker'

const firstName = faker.name.firstName()
const lastName = faker.name.lastName()
const fullName = `${firstName} ${lastName}`

const selectCard = () =>
{
    console.log()
}
</script>

<template>
    <div class="card" @click="selectCard">
        <div class="card-image">
            <img :src="faker.internet.avatar()" alt="" srcset="" />
        </div>
        
        <div class="card-details">
            <p class="card-details-name">{{ fullName }}</p>
            <p class="card-details-job">{{ faker.name.jobTitle() }}, {{ faker.name.jobArea() }}</p>
            <p class="card-details-quote">"test test test "</p>
        </div>        
    </div>
</template>

<style scoped lang="postcss">
.card{
    @apply overflow-hidden bg-slate-100 p-8 ;
    
    &-image{
        img{
            @apply  object-contain invisible;
        }
    }

    &-details{
        @apply flex flex-col gap-2 pt-6 text-center invisible;

        &-name{
            @apply text-3xl font-thin tracking-wider text-slate-800;
        }

        &-job{
            @apply -mt-2 text-xs font-bold text-yellow-700;
        }

        &-quote{
            @apply pt-4 text-lg italic text-slate-800;
        }
    }

}
</style>