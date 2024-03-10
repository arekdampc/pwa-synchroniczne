<template>
  <div class="promo-carrousel" ref="carouselContainer">
    <div class="carousel-items-container" :style="{ transform: `translateX(-${activeSection * 100}%)` }">
      <div class="carousel-item" v-for="(group, index) in slideGroups" :key="index">
        <div v-for="(item, slideIndex) in group" :key="slideIndex" class="scaled-image">
          <img :src="item.image" :alt="item.caption" />
          <div class="image-caption">{{ item.caption }}</div>
        </div>
      </div>
    </div>
    <button class="carousel-control left" @click="prevSection" :class="{ 'hidden': activeSection === 0 }">&lt;</button>
    <button class="carousel-control right" @click="nextSection" :class="{ 'hidden': activeSection === slideGroups.length - 1 }">&gt;</button>
  </div>
</template>

<style lang="scss" src="./promoCarrousel.scss" scoped></style>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const carouselContainer = ref(null);

const chunkArray = (array, size) => {
  return array.reduce((chunks, item, index) => {
    if (index % size === 0) {
      chunks.push([item]);
    } else {
      chunks[chunks.length - 1].push(item);
    }
    return chunks;
  }, []);
};

const slideGroups = ref(chunkArray([
  { image: 'promoCarrousel/prom1.png', caption: 'SUPERszybkie, SUPERmocne. Poznaj nowe karty graficzne.' },
  { image: 'promoCarrousel/prom2.png', caption: 'Kup Samsung Galaxy S24' },
  { image: 'promoCarrousel/prom3.png', caption: 'MacBook Air' },
  { image: 'promoCarrousel/prom4.png', caption: 'Premiera Nothing Phone (2a)' },
  { image: 'promoCarrousel/prom5.png', caption: 'Premiera Xiaomi 14 Ultra' },
  { image: 'promoCarrousel/prom6.png', caption: 'Goździk to za mało?' },
  { image: 'promoCarrousel/prom7.png', caption: 'Premiera SPARK 20 PRO+' },
  { image: 'promoCarrousel/prom8.png', caption: 'Graj, jak chcesz' },
  { image: 'promoCarrousel/prom9.png', caption: 'Zgarnij mysz TUF Gaming M4 Air' },
], 3));

const activeSection = ref(0);

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

onMounted(() => {
  // dodatkowe inicjalizacje 
});

onBeforeUnmount(() => {
  // czyszczenie 
});
</script>
