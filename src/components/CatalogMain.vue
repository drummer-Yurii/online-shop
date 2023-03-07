<template>
    <div class="catalog">
        <h1>Catalog</h1>
        <catalog-item></catalog-item>
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

</style>