<script setup>
import AuthLayout from '@/Layouts/AuthLayout.vue';
import CalendarSelector from '@/Components/Calendar/CalendarSelector.vue';
import { Link, Head } from '@inertiajs/inertia-vue3';

const catalog = defineProps({
  catalog: Array,
  shops: Array
})
</script>

<template>
  <Head title="UserList" />
  
  <AuthLayout>
    <div class="wrapper-home">
      <div class="calendar-box">
        <CalendarSelector 
          
        />
      </div>
      <div class="my-content mt-5 p-2.5" v-for="catalogItem in catalog.catalog" :key="catalogItem.id">
        <h1 class="text-stone-700 text-lg font-bold underline underline-offset-8">
          {{ catalogItem.name }}
        </h1>
        <div class="text-sm text-stone-500 mt-1">
          {{ catalogItem.list_data }}
        </div>
        <div v-if="catalog.shops.length" class="w-full flex flex-col mt-6">
          <div v-for="(shop, idx) in catalog.shops" :key="shop.id" class="hover:cursor-pointer mt-2 flex items-center justify-between w-full">
            <div class="flex items-center justify-start w-[60%] text-stone-600">
              {{ idx + 1 }}.  &nbsp;  {{ shop.shop_name }}
            </div>
            <div class="flex items-center justify-start w-[20%] text-stone-600">
              0 &nbsp;/&nbsp; 10
            </div>
            <div class="flex items-center justify-end w-[20%]">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-right" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"/>
              </svg>
            </div>
          </div>
        </div>
        <div v-else class="w-full flex flex-col mt-6">
          <div class="text-stone-600 font-bold text-lg">
            You don't have Shops for this list.
            {{catalogItem.id}}
          </div>
          <Link
            :href="route('shops.create')"
            class="hover:underline  hover:underline-offset-8 hover:text-sky-400 text-lg text-sky-500 mt-3 font-bold"
            >Create shop
          </Link>
        </div>
      </div>
    </div>
  </AuthLayout>
</template>

<style>

</style>