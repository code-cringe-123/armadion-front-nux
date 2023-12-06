<template>
    <div class="catalog-wrapper">
        <div class="products-wrapper">
            <div class="products" v-for="product in products" :key="product.id">
                <Product :product="product" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const products = ref([])

// загрузка данных из products.json
const loadProducts = async () => {
    try {
        const response = await fetch('/products.json')
        const data = await response.json()
        products.value = data
    } catch (error) {
        console.error('Ошибка загрузки данных:', error)
    }
}
// const { data: products } = await useFetch('/public/products.json')
onMounted(() => {
    loadProducts()
})
</script>

<style lang="scss">
.catalog-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-width: 1180px;

    @media screen and (max-width: 1024px) {
        width: 100vw;
    }

    @media screen and (max-width: 768px) {
        width: 355px;
    }
}

.products-wrapper {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;

    @media screen and (max-width: 1200px) {
        width: 100vw;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 15px;
    }

    @media screen and (max-width: 960px) {
        width: 100vw;
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 15px 10px;
    }

    @media screen and (max-width: 768px) {
        width: 100vw;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
    }
}

.products {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
