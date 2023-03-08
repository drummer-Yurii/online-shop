<template>
    <div class="catalog">
        <h1>Catalog</h1>
        <div class="catalog__list">
            <catalog-item 
                v-for="product in PRODUCTS"
                :key="product.article"
                :product_data="product"
                @addToCart="addToCart"
            />
        </div>
    </div>
</template>

<script>
import CatalogItem from './CatalogItem.vue'
import { mapActions, mapGetters } from 'vuex';
export default {
    name: 'CatalogMain',
    components: {
        CatalogItem
    },
    data() {
        return {
           
        }
    },
    computed: {
        ...mapGetters([
            'PRODUCTS'
        ])
    },
    methods: {
        ...mapActions([
            'GET_PRODUCTS_FROM_API',
            'ADD_TO_CART'
        ]),
        addToCart(data) {
            this.ADD_TO_CART(data);
        }
    },
    mounted() {
        this.GET_PRODUCTS_FROM_API()
    }
}
</script>

<style lang="scss">
.catalog {
    padding-top: 60px;

    &__list {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
    }
}
</style>