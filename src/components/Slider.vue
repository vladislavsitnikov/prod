<script setup>
import { ref, computed } from 'vue';

const images = ref([
  'https://via.placeholder.com/150',
  'https://via.placeholder.com/250',
  'https://via.placeholder.com/350',
  'https://via.placeholder.com/450',
  'https://via.placeholder.com/550',
  'https://via.placeholder.com/650',
]);
const currentIndex = ref(0);
const thumbnailsPerPage = 4;

const currentImage = computed(() => images.value[currentIndex.value]);
const totalThumbnails = computed(() => images.value.length);
const totalPages = computed(() => Math.ceil(totalThumbnails.value / thumbnailsPerPage));
const currentPage = computed(() => Math.ceil((currentIndex.value + 1) / thumbnailsPerPage));
const firstIndex = computed(() => {
  const page = currentPage.value;
  return page <= totalPages.value - 1 ? (page - 1) * thumbnailsPerPage : totalThumbnails.value - thumbnailsPerPage;
});
const visibleThumbnails = computed(() => {
  const startIndex = firstIndex.value;
  return images.value.slice(startIndex, startIndex + thumbnailsPerPage);
});

const setCurrentImage = (index) => {
  currentIndex.value = index;
};
const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + totalThumbnails.value) % totalThumbnails.value;
};
const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % totalThumbnails.value;
};
</script>
<template>
  <div class="slider">
    <div class="main-slider">
      <img :src="currentImage" alt="Main Slide" />
    </div>
    <div class="thumbnail-slider">
      <div class="controls">
        <button @click="prevSlide"><img class="arrow" src="../assets/arrow.svg"></button>
      </div>
      <div class="thumbnail-container">
        <div
          v-for="(image, index) in visibleThumbnails"
          :key="index"
          @click="setCurrentImage(index + firstIndex)"
          :class="{ active: index === currentIndex % thumbnailsPerPage }"
          class="thumbnail"
        >
          <img :src="image" alt="Thumbnail" />
        </div>
      </div>
      <div class="controls">
        <button @click="nextSlide"><img src="../assets/arrow.svg"></button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.slider {
  display: flex;
  flex-direction: column;
  align-items: center;

  .main-slider img {
    width: 560px;
    height: 560px;
    object-fit: cover;
    margin-bottom: 10px;
  }

  .controls {
    margin-bottom: 10px;
    button{
      border-style: none;
      outline-style: none;
      background-color: inherit;
      cursor: pointer;
      .arrow{
        transform: rotate(180deg);
      }
      img{
        object-fit: cover;
      }
    }
  }

  .thumbnail-slider {
    display: flex;
    align-items: center;

    .thumbnail-container {
      display: flex;

      .thumbnail {
        margin: 0 5px;
        cursor: pointer;

        img {
          width: 120px;
          height: 120px;
          object-fit: cover;
          border: 2px solid transparent;
        }

        &.active img {
          border: 1px solid #333;
        }
      }
    }
  }
}
@media (max-width: 1280px){
  .main-slider img {
    width: 360px!important;
    height: auto!important;
  }
  .thumbnail {
    img {
      width: 60px!important;
      height: 60px!important;
    }
  }
}
@media (max-width: 380px){
  .main-slider img {
    width: 340px!important;
    height: auto!important;
  }
  .thumbnail {
    img {
      width: 60px!important;
      height: 60px!important;
    }
  }
}
</style>
