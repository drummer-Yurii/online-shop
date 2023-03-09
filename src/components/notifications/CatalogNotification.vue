<template>
    <div class="catalog-notification">
        <div class="catalog-notification__content" v-for="message in messages" :key="message.id">
            <span>{{ message.name }}</span>
            <i class="material-icons">check_circle</i>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CatalogNotification',
    props: {
        messages: {
            type: Array,
            default() {
                return []
            }
        }
    }
}
</script>

<style lang="scss">
.catalog-notification {
    position: fixed;
    top: 80px;
    right: 16px;
    z-index: 10;

    &__content {
        padding: $padding*3;
        border-radius: 4px;
        color: $color-light;
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 16px;
        margin-bottom: $margin*2;
        background-color: $color-special;
        max-width: 200px;
        text-align: left;
        gap: 10px;
        font-size: 12px;
    }
}
</style>