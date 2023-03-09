<template>
    <div class="catalog-cart">
        <h1>Cart</h1>
        <cart-item-wrapper 
            v-if="CART.length" 
            :cart_data="CART" 
        />
    </div>
</template>

<script>
import { mapGetters } from 'vuex';
import CartItemWrapper from './CartItemWrapper.vue';
export default {
    name: 'CatalogCart',
    components: {
        CartItemWrapper
    },
    computed: {
        ...mapGetters([
            'CART'
        ])
    },
}
</script>

<style lang="scss" scoped></style>