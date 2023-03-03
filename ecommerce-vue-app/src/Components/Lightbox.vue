<template>
<div class="main-lightbox-container">
        <teleport to="body">
            <div class="lightbox">
                <span @click="closeLightBox" class="lightboxClose">&times;</span>
                <div class="lightboxBody">
                    <Carousel id="carousel"/>
                </div>
            </div>
        </teleport>
    </div>
</template>

<script>
import Carousel from './Carousel.vue';

export default {
    name: 'Lightbox',
    components: {
        Carousel
    },
    props: {
    lightbox: {
      type: Boolean,
      required: true
    }
  },
    methods: {
        closeLightBox() {
            this.$emit('update:lightBox', false)
        }
    }
}
</script>

<style lang="scss">
@import './Lightbox.scss';
</style>