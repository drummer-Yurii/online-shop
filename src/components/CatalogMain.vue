<template>
    <div class="catalog">
        <h1>Catalog</h1>
        <div class="catalog__li">
            <catalog-item></catalog-item>
        </div>
    </div>
</template>

<script>
import CatalogItem from './CatalogItem.vue'
export default {
    name: 'CatalogMain',
    components: {
        CatalogItem
    },
}
</script>

<style lang="scss" scoped>
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