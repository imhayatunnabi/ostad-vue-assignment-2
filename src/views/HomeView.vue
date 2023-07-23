<template>
  <div id="carouselExample" class="carousel slide">
    <div class="carousel-inner">
      <div v-for="(image, index) in images" :key="index" :class="['carousel-item', index === 0 ? 'active' : '']">
        <img :src="image" class="d-block w-100" alt="Slide {{ index + 1 }}">
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const images = ref([
  require('@/assets/image1.jpg'),
  require('@/assets/image2.jpg'),
  require('@/assets/image3.jpg'),
]);

const currentIndex = ref(0);

const currentImage = computed(() => images.value[currentIndex.value]);

const nextImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.value.length;
};

const prevImage = () => {
  currentIndex.value = (currentIndex.value - 1 + images.value.length) % images.value.length;
};
</script>

<style>
/* Add your custom styles here */
</style>
