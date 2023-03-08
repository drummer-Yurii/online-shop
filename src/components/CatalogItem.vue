<template>
    <div class="catalog-item">
        <div class="catalog-item__image-wrap">
            <img class="catalog-item__image" :src="require('../assets/images/' + product_data.image)" alt="">
        </div>
        <p class="catalog-item__name">{{ product_data.name }}</p>
        <p class="catalog-item__price">{{ product_data.price }} UAH</p>
        <button 
            class="catalog-item__btn"
            @click="addToCart"
        >
            Add to cart
        </button>
    </div>
</template>

<script>
export default {
    name: 'CatalogItem',
    components: {},
    props: {
        product_data: {
            type: Object,
            default() {
                return {}
            }
        }
    },
    methods: {
        addToCart() {
            this.$emit('sendArticle', this.product_data.article)
        }
    }
}
</script>

<style lang="scss">
    .catalog-item {
        flex-basis: 25%;
        box-shadow: 0 0 8px 0 $color-shadow;
        padding: $padding*2;
        margin: 0 auto $margin*2;
        min-width: 150px;
        @media (max-width: 470px) {
            padding: $padding;
        }
        &__image-wrap {
            width: 100px;
            overflow: hidden;
            margin: 0 auto;
        }
        &__image {
            object-fit: cover;
            object-position: center;
            width: 100%;
            height: 100%;
        }
    }
</style>