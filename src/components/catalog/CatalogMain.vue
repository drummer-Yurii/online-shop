<template>
    <div class="catalog">
        <router-link :to="{name: 'cart'}">
            <div class="catalog__link">Cart: {{ CART.length }}</div>
        </router-link>
        <h1>Catalog</h1>
        <catalog-notification 
            :messages="messages"
        />
        <catalog-select 
            :options="categories"
            :selected="selected"
            @select="sortByCategories"
        />
        <div class="catalog__list">
            <catalog-item 
                v-for="product in filteredProducts"
                :key="product.article"
                :product_data="product"
                @addToCart="addToCart"
            />
        </div>
    </div>
</template>

<script>
import CatalogItem from './CatalogItem.vue';
import CatalogSelect from './CatalogSelect.vue';
import CatalogNotification from '../notifications/CatalogNotification.vue';
import { mapActions, mapGetters } from 'vuex';
export default {
    name: 'CatalogMain',
    components: {
        CatalogItem,
        CatalogSelect,
        CatalogNotification
    },
    data() {
        return {
           categories: [
                {name: 'All', value: 'All'},
                {name: 'Male', value: 'M'},
                {name: 'Female', value: 'F'},
           ],
           sortedProducts: [],
           selected: 'All',
           messages: []
        }
    },
    computed: {
        ...mapGetters([
            'PRODUCTS',
            'CART'
        ]),
        filteredProducts() {
            if (this.sortedProducts.length) {
                return this.sortedProducts;
            } else {
                return this.PRODUCTS;
            }
        }  
    },
    methods: {
        ...mapActions([
            'GET_PRODUCTS_FROM_API',
            'ADD_TO_CART'
        ]),
        addToCart(data) {
            this.ADD_TO_CART(data)
            .then(() => {
                let timeStamp = Date.now().toLocaleString();
                this.messages.unshift({name: 'The product has been added to the cart', id: timeStamp})
            })
        },
         sortByCategories(category) {
            this.sortedProducts = [];
            let select = this;
            this.PRODUCTS.map(function (item) {
                if (category.name === item.category) {
                    select.sortedProducts.push(item);
                }
            });
            this.selected = category.name;
        },
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