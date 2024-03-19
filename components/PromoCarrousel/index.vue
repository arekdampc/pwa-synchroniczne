<template>
  <div
    v-if="!pending && !error && slideGroups.length > 0"
    class="promo-carrousel"
    ref="carouselContainer"
  >
    <div
      class="carousel-items-container"
      :style="{ transform: `translateX(-${activeSection * 100}%)` }"
    >
      <div
        class="carousel-item"
        v-for="(group, index) in slideGroups"
        :key="index"
      >
        <div
          v-for="(item, slideIndex) in group"
          :key="slideIndex"
          class="scaled-image"
        >
          <img :src="item.image" :alt="item.caption" />
          <div class="image-caption">{{ item.caption }}</div>
        </div>
      </div>
    </div>
    <button
      class="carousel-control left"
      @click="prevSection"
      :class="{ hidden: activeSection === 0 }"
    >
      &lt;
    </button>
    <button
      class="carousel-control right"
      @click="nextSection"
      :class="{ hidden: activeSection === slideGroups.length - 1 }"
    >
      &gt;
    </button>
  </div>
</template>

<style lang="scss" src="./promoCarrousel.scss" scoped></style>

<script setup>
import { ref } from 'vue';
import { useAsyncData } from 'nuxt/app';

const carouselContainer = ref(null);
const activeSection = ref(0);

const chunkArray = (array, size) => {
  return array.reduce((chunks, item, index) => {
    const chunkIndex = Math.floor(index / size);
    chunks[chunkIndex] = [...(chunks[chunkIndex] || []), item];
    return chunks;
  }, []);
};

const {
  data: promoData,
  pending,
  error,
} = useAsyncData('promoCarrouselData', () =>
  fetch('http://localhost:3001/promo-carrousel').then(res => res.json())
);

const slideGroups = ref([]);
promoData.value && (slideGroups.value = chunkArray(promoData.value, 3));

const prevSection = () => {
  if (activeSection.value > 0) {
    activeSection.value -= 1;
  }
};

const nextSection = () => {
  if (activeSection.value < slideGroups.value.length - 1) {
    activeSection.value += 1;
  }
};
</script>
