<template>
    <div class="catalog-page-container">
        <Catalog-menu class="catalog-page-container-menu" />
        <Catalog />
    </div>
</template>

<script setup>
</script>

<style lang="scss">
.catalog-page-container {
    margin-top: 195px;
    display: flex;
    flex-direction: row;
    /* align-items: center; */
    justify-content: center;
    @media screen and (max-width: 1024px) {
        padding: 0 20px;
    }
    @media screen and (max-width: 666px) {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}

// .catalog-page-container-menu {
    
// }
</style>
