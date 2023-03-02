<template>
     <div class="home-container">
        <Nav @toggle-cart='toggleCart' :count="count" :add-cart="addCart" />
        <div class="product-main-section">
          <Cart :add-cart="addCart" @update:addCart="updateAddCart" v-if="showCart" />
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

export default {
  name: 'Home',
  components: {
    Nav,
    Cart
  },
  data() {
    return {
      showCart: false,
      addCart: false,
      count: 0
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
    }
  }
}
</script>

<style lang="scss">
@import './Home.scss';
</style>