<template>
     <div class="home-container">
        <Nav @toggle-cart='toggleCart' />
        <div class="product-main-section">
          <Cart v-if="showCart" />
          <div class="product-images-section">
            <div class="product-image">
              <img src="/public/images/image-product-1.jpg" />
            </div>
            <div class="product-image-thumbnails">
              <img src="/public/images/image-product-1-thumbnail.jpg" />
              <img src="/public/images/image-product-2-thumbnail.jpg" />
              <img src="/public/images/image-product-3-thumbnail.jpg" />
              <img src="/public/images/image-product-4-thumbnail.jpg" />
            </div>
          </div>
          <div class="product-description-section">
            <div class="description">
              <h3>Sneaker company</h3>
              <h1>Fall Limited Edition Sneakers</h1>
              <p>These low-profile sneakers are your perfect casual wear
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
                <button id="minus">-</button>
                <p id="count">0</p>
                <button id="plus">+</button>
              </div>
              <button id="cart"><span><fa id="cart-icon" icon="cart-shopping" /></span>Add to cart</button>
            </div>
          </div>
        </div>
    </div>
</template>

<script>
import Nav from '../Components/Nav.vue';
import Cart from '../Components/Cart.vue';

export default {
  name: 'Home',
  components: {
    Nav,
    Cart
  },
  data() {
    return {
      showCart: false
    }
  },
  methods: {
    toggleCart() {
      this.showCart = !this.showCart
    }
  }
}
</script>

<style lang="scss">
@import './Home.scss';
</style>