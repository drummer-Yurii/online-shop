<template>
    <div class="catalog">
        <router-link :to="{name: 'cart'}">
            <div class="catalog__link">Cart: {{ CART.length }}</div>
        </router-link>
        
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
            'PRODUCTS',
            'CART'
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
    &__link {
        position: absolute;
        top: 10px;
        right: 10px;
        padding: $padding*2;
        border: 1px solid #ddd;
        cursor: pointer;
    }
}
</style>