<script setup>
import { RouterLink, RouterView } from "vue-router";
import Dropdown from "./components/Dropdown.vue";
</script>

<template>
  <header class="bg-yellow-600 px-12 py-4 flex items-center">
    <div class="w-1/2">
      <p class="text-white font-medium text-xl">Roll your dice!</p>
    </div>
    <div class="w-1/2 text-right">
      <Dropdown />
    </div>
  </header>

  <RouterView />
</template>
