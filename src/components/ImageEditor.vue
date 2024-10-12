<template>
  <div class="bg-gray-800 p-6 rounded-lg shadow-lg">
    <div class="mb-6">
      <label for="image-upload" class="flex items-center justify-center w-full h-32 border-2 border-orange-500 border-dashed rounded-lg cursor-pointer bg-gray-700 hover:bg-gray-600 transition-colors">
        <div class="flex flex-col items-center">
          <Upload class="text-orange-500 mb-2" />
          <span class="text-sm text-orange-300">Upload your image</span>
        </div>
        <input id="image-upload" type="file" class="hidden" @change="handleImageUpload" accept="image/*" />
      </label>
    </div>

    <div v-if="image" class="space-y-4">
      <div class="relative">
        <img
          :src="image"
          alt="Uploaded image"
          class="w-full h-auto rounded-lg"
          :style="{ filter: filter }"
        />
      </div>
      <div class="flex flex-wrap gap-2">
        <button @click="applyFilter('none')" class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600">Normal</button>
        <button @click="applyFilter('grayscale(100%)')" class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600">Grayscale</button>
        <button @click="applyFilter('sepia(100%)')" class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600">Sepia</button>
        <button @click="applyFilter('invert(100%)')" class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600">Invert</button>
        <button @click="applyFilter('hue-rotate(180deg)')" class="px-4 py-2 bg-orange-500 text-white rounded hover:bg-orange-600">Hue Rotate</button>
      </div>
      <button @click="downloadImage" class="flex items-center justify-center w-full px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600">
        <Download class="mr-2" />
        Download Spooky Image
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Upload, Download } from 'lucide-vue-next';

const props = defineProps(['image']);
const emit = defineEmits(['update:image']);

const filter = ref('none');

const handleImageUpload = (event) => {
  const file = event.target.files?.[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = (e) => emit('update:image', e.target?.result);
    reader.readAsDataURL(file);
  }
};

const applyFilter = (selectedFilter) => {
  filter.value = selectedFilter;
};

const downloadImage = () => {
  if (props.image) {
    const link = document.createElement('a');
    link.href = props.image;
    link.download = 'spooky_image.png';
    link.click();
  }
};
</script>