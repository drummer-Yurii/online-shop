<template>
    <div class="catalog-popup__wrapper">
        <div class="catalog-popup">
            <div class="catalog-popup__header">
                <span>Title</span>
                <span>
                    <i class="material-icons">close</i>
                </span>
            </div>
            <div class="catalog-popup__content">
                <slot></slot>
            </div>
            <div class="catalog-popup__footer">
                <button class="btn">Close</button>
                <button class="btn">Add to cart</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CatalogPopup'
}
</script>

<style lang="scss">
.catalog-popup {
    position: fixed;
    padding: $padding*2;
    top: 250px;
    width: 400px;
    box-shadow: 0 0 $padding*2 0 $color-shadow;
    left: calc(50% - 200px);
    z-index: 33;
    background-color: $color-light;

    &__header, &__footer {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    &__wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: $color-popup;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        z-index: 30;
        max-height: 100%;
    }
    &__content {
        display: flex;
        justify-content: center;
        align-items: center;
    }
}
</style>