<script setup lang="ts">
import { ref } from 'vue';
import { useFetch } from '#app';

interface Image {
  id: number;
  src: string;
  caption: string;
  alt: string;
}

const { data: images, pending, error } = useFetch<Image[]>('http://localhost:3001/carrousel');

const activeIndex = ref(0);
const startX = ref(0);
const endX = ref(0);

function startSwipe(event) {
  startX.value = event.touches[0].clientX;
}

function onSwipe(event) {
  endX.value = event.touches[0].clientX;
}

function endSwipe() {
  if (startX.value - endX.value > 50) {
    // przesunięcie palcem w lewo
    nextImage();
  } else if (startX.value - endX.value < -50) {
    // przesunięcie palcem w prawo
    prevImage();
  }
}

const nextImage = () => {
  activeIndex.value = (activeIndex.value + 1) % images.value.length;
};

const prevImage = () => {
  activeIndex.value =
    (activeIndex.value - 1 + images.value.length) % images.value.length;
};

const setActiveIndex = (index: number) => {
  activeIndex.value = index;
};
</script>

<template>
  <div class="carousel" v-if="!pending && !error">
    <div
      class="carousel-container"
      @touchstart="startSwipe"
      @touchmove="onSwipe"
      @touchend="endSwipe"
    >
      <button class="carousel-control left is-hidden-touch" @click="prevImage">
        &lt;
      </button>
      <div
        v-for="(image, index) in images"
        :key="image.id"
        class="carousel-item"
        :style="{ display: index === activeIndex ? 'block' : 'none' }"
      >
        <img :src="image.src" :alt="image.alt" />
      </div>
      <button class="carousel-control right is-hidden-touch" @click="nextImage">
        &gt;
      </button>
    </div>
    <div class="carousel-indicators is-hidden-touch">
      <span
        v-for="(image, index) in images"
        :key="image.id"
        class="carousel-caption"
        :class="{ 'is-active': index === activeIndex }"
        @click="setActiveIndex(index)"
      >
        {{ image.caption }}
      </span>
    </div>
  </div>
  <div v-if="pending">Ładowanie...</div>
  <div v-if="error">Wystąpił błąd podczas ładowania danych: {{ error.message }}</div>
</template>

<style lang="scss" scoped>
@import './carrousel.scss';
</style>
