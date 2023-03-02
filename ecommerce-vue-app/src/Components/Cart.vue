<template>
    <div class="cart-main-section">
        <div class="cart-heading-section">
            <h4>Cart</h4>
        </div>
        <div v-if="addCart === true" class="cart-product-section">
            <div class="cart-product-left">
                <img src="/public/images/image-product-1-thumbnail.jpg" />
            </div>
            <div class="cart-product-right">
                <h4>Fall Limited Edition Sneakers</h4>
                <div class="cart-pricing">
                    <p>$125.00 x {{ count }}</p><span>${{ sum }}</span>
                    <fa @click="remove" id="trash-icon" icon="trash-can" />
                </div>
            </div>
        </div>
        <div v-if="addCart" class="cart-checkout-section">
            <button id="checkout">Checkout</button>
        </div>
        <div v-if="addCart === false" class="cart-product-section">
            <p id="empty-message">Your Cart is empty.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Cart',
    props: {
        count: {
        type: Number,
        required: true,
        default: 0
        },
        addCart: {
            type: Boolean,
            required: true
        }
    }, 
    data() {
        return {
            sum: ''
        }
    },
    methods: {
        remove() {
            this.$emit('update:addCart', false);      
        },
        summary() {
            this.sum = (this.count * 125).toFixed(2);
        }
    },
    watch: {
        count(newCount) {
            this.summary();
            if (newCount === 0) {
                this.remove();
            } 
        }
    },
    created() {
        this.summary();
    }
}
</script>

<style lang="scss">
@import './Cart.scss';
</style>