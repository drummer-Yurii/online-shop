<template>
    <div class="catalog-wrapper">
        <p>{{ title }}</p>
        <catalog-main></catalog-main>
        <catalog-cart></catalog-cart>
    </div>
</template>

<script>
import CatalogMain from './CatalogMain.vue';
import CatalogCart from './CatalogCart.vue';
export default {
    name: 'CatalogWrapper',
    components: {
        CatalogMain,
        CatalogCart
    },
    props: {},
    data() {
        return {
            title: 'Main Wrapper'
        }
    },
    computed: {},
    methods: {},
    watch: {},
    mounted() {
        console.log('I like Vue');
    }
}
</script>

<style lang="scss" scoped>
    .catalog-wrapper {
        width: 900px;
        margin: 0 auto;
    }
</style>