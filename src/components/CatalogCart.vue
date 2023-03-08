<template>
    <div class="catalog-cart">
        <h1>Cart</h1>
        <catalog-cart-item 
            v-for="item in cart_data"
            :key="item.article"
            :cart_item_data="item"
        />
    </div>
</template>

<script>
import CatalogCartItem from './CatalogCartItem.vue';
export default {
    name: 'CatalogCart',
    components: {
        CatalogCartItem
    },
    props: {
        cart_data: {
            type: Array,
            default() {
                return []
            }
        }
    }
}
</script>

<style lang="scss" scoped></style>