<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Todos from './components/Todos.vue'

</script>

<template>
  <div class="h-screen  flex items-center justify-center bg-blue-100">
    <div class="w-96 rounded-md shadow-lg flex justify-center items-center flex-col bg-white pb-5 md:w-1/2  sm:w-96">
      <h1 class="text-xl font-bold p-3">TODO LIST</h1>
      <Todos/>
    </div>
    
  </div>
  <RouterView />
</template>
