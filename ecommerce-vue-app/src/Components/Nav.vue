<template>
    <div class="navbar-container">
       <div class="logo-section">
           <img src="public/images/logo.svg" />
       </div>
       <nav>
           <ul>
               <li><a href="#">Collections</a></li>
               <li><a href="#">Men</a></li>
               <li><a href="#">Women</a></li>
               <li><a href="#">About</a></li>
               <li><a href="#">Contact</a></li>
           </ul>
       </nav>
       <div class="cart-section">
           <img @click="toggleCart" src="public/images/icon-cart.svg"><span v-if="count > 0" id="cart-count">{{ count }}</span><img/>
           <img src="public/images/image-avatar.png" />
       </div>
   </div>
</template>

<script>
import Cart from './Cart.vue';

export default {
    name: 'Nav',
    components: {
    Cart
  }, 
  props: {
    count: {
        type: Number,
        required: true,
        default: 0
    }
  },
  methods: {
    toggleCart() {
        this.$emit('toggle-cart')
    }
  }
}
</script>

<style lang="scss">
@import './Nav.scss';
</style>