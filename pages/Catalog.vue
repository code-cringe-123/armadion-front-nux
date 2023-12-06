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

    @media screen and (max-width: 425px) {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
}

// .catalog-page-container-menu {
//   margin-right: 20px;
// }
</style>
