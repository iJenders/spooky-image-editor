<template>
  <header class="bg-gray-800 py-4">
    <div class="container mx-auto px-4 flex justify-between items-center">
      <div class="flex items-center space-x-2">
        <Ghost class="text-orange-500" :size="32" />
        <span class="text-xl font-bold text-orange-500">Spooky Editor</span>
      </div>
      <nav>
        <ul class="flex space-x-4">
          <li><a href="#" class="text-orange-300 hover:text-orange-500">Home</a></li>
          <li><a href="#" class="text-orange-300 hover:text-orange-500">Gallery</a></li>
          <li><a href="#" class="text-orange-300 hover:text-orange-500">About</a></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { Ghost } from 'lucide-vue-next';
</script>