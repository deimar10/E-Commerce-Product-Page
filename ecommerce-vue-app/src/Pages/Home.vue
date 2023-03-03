<template>
     <div class="home-container">
        <Nav @toggle-cart='toggleCart' :count="count" :add-cart="addCart" />
        <div class="product-main-section">
          <Cart :count="count" :add-cart="addCart" @update:addCart="updateAddCart" v-if="showCart" />
          <div class="product-images-section">
            <div class="product-image">
              <img src="/images/image-product-1.jpg" @click="toggleLightBox" v-if="thumbnails.thumbnail1 === true"/>
              <img src="/images/image-product-2.jpg" @click="toggleLightBox" v-if="thumbnails.thumbnail2 === true"/>
              <img src="/images/image-product-3.jpg" @click="toggleLightBox" v-if="thumbnails.thumbnail3 === true"/>
              <img src="/images/image-product-4.jpg" @click="toggleLightBox" v-if="thumbnails.thumbnail4 === true"/>
              <Lightbox v-if="lightbox" :lightbox="lightbox" @update:lightBox="updateLighBox" />
            </div>
            <div class="product-image-thumbnails">
              <img src="/images/image-product-1-thumbnail.jpg" @click="updateThumbnail(1)" :style="thumbnails.thumbnail1 ? styleObject : null"/>
              <img src="/images/image-product-2-thumbnail.jpg" @click="updateThumbnail(2)" :style="thumbnails.thumbnail2 ? styleObject : null"/>
              <img src="/images/image-product-3-thumbnail.jpg" @click="updateThumbnail(3)" :style="thumbnails.thumbnail3 ? styleObject : null" />
              <img src="/images/image-product-4-thumbnail.jpg" @click="updateThumbnail(4)" :style="thumbnails.thumbnail4 ? styleObject : null" />
            </div>
          </div>
          <div class="product-description-section">
            <div class="description">
              <h3>Sneaker company</h3>
              <h1>Fall Limited Edition Sneakers</h1>
              <p>
                These low-profile sneakers are your perfect casual wear
                companion. Featuring a durable rubber outer sole, they'll
                withstand everything the weather can offer.
              </p>
            </div>
            <div class="price-section">
              <p>$125.00</p>
              <label>50%</label>
            </div>
            <p id="actual-price">$250.00</p>
            <div class="home-cart-section">
              <div class="amount-section">
                <button @click="decrement" id="minus">-</button>
                <p id="count">{{ count }}</p>
                <button @click="increment" id="plus">+</button>
              </div>
              <button @click="addToCart" id="cart"><span><fa id="cart-icon" icon="cart-shopping" /></span>Add to cart</button>
            </div>
          </div>
        </div>
    </div>
</template>

<script>
import Nav from '../Components/Nav.vue';
import Cart from '../Components/Cart.vue';
import Carousel from '../Components/Carousel.vue';
import Lightbox from '../Components/Lightbox.vue';

export default {
  name: 'Home',
  components: {
    Nav,
    Cart,
    Carousel,
    Lightbox
},
  data() {
    return {
      showCart: false,
      addCart: false,
      lightbox: false,
      count: 0,
      thumbnails: {
        thumbnail1: true,
        thumbnail2: false,
        thumbnail3: false,
        thumbnail4: false
      }
    }
  },
  methods: {
    toggleCart() {
      this.showCart = !this.showCart
    },
    addToCart() {
      if(this.count > 0) {
        this.addCart = true
        this.$emit('add-to-cart', this.addCart) 
      } else {
        alert("Cant add 0 items to cart!")
      }
    },
    updateAddCart(value) {
      this.addCart = value;
    },
    increment() {
      if(this.count >= 5) {
        null
      } else  {
        this.count++;
      }      
    },
    decrement() {
      if(this.count === 0) {
        null;
      } else  {
        this.count--;
      }
    },
    toggleLightBox() {
      this.lightbox = true
    },
    updateLighBox(value) {
      this.lightbox = value;
    },
    updateThumbnail(thumbnailNum) {
      Object.keys(this.thumbnails).forEach(key => {
        if (key === 'thumbnail' + thumbnailNum) {
          this.thumbnails[key] = true;
        } else {
          this.thumbnails[key] = false;
        }
      });
    }
  },
  mounted() {
    const image1 = new Image();
    image1.src = '/images/image-product-1.jpg';
    const image2 = new Image();
    image2.src = '/images/image-product-2.jpg';
    const image3 = new Image();
    image3.src = '/images/image-product-3.jpg';
    const image4 = new Image();
    image4.src = '/images/image-product-4.jpg';
  },
  computed: {
    styleObject() {
      return {
        border: '3px solid hsl(26, 100%, 55%)',
        opacity: '40%' 
      }
    }
  }
}
</script>

<style lang="scss">
@import './Home.scss';
</style>