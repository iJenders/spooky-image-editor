<template>
  <div class="min-h-screen bg-gray-900 text-orange-50 flex flex-col">
    <Header />
    <main class="flex-grow container mx-auto px-4 py-8">
      <h1 class="text-4xl font-bold text-orange-500 mb-8 text-center">Spooky Halloween Image Editor</h1>
      <ImageEditor :image="image" @update:image="setImage" />
    </main>
    <footer class="bg-gray-800 py-4">
      <div class="container mx-auto px-4 flex justify-between items-center">
        <p>&copy; 2023 Spooky Image Editor</p>
        <div class="flex space-x-4">
          <Ghost class="text-orange-500" />
          <Moon class="text-orange-500" />
          <Skull class="text-orange-500" />
          <Zap class="text-orange-500" />
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Ghost, Moon, Skull, Zap } from 'lucide-vue-next';
import ImageEditor from './components/ImageEditor.vue';
import Header from './components/Header.vue';

const image = ref(null);

const setImage = (newImage) => {
  image.value = newImage;
};
</script>