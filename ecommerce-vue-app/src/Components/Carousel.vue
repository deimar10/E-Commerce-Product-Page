<template>
    <div class="main-carousel-container">
        <Swiper>
            <SwiperSlide v-for="photo in photos" :key="photo">
                <img :src="`${photo}`" />
            </SwiperSlide>
        </Swiper>
    </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";

const photos = [
    "/public/images/image-product-1.jpg",
    "/public/images/image-product-2.jpg",
    "/public/images/image-product-3.jpg",
    "/public/images/image-product-4.jpg"
];

export default {
    name: 'Carousel',
    components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      photos: [
        "/public/images/image-product-1.jpg",
        "/public/images/image-product-2.jpg",
        "/public/images/image-product-3.jpg",
        "/public/images/image-product-4.jpg",
      ]
    }
  }
}
</script>
