<template>
    <div class="catalog-wrapper">
        <router-view />
    </div>
</template>

<script>
export default {
    name: 'CatalogWrapper'
}
</script>

<style lang="scss">
    .catalog-wrapper {
        max-width: 900px;
        margin: 0 auto;
        height: inherit;
    }
</style>