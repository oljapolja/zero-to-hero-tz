<template>
    <div class="row">
        <ProductItem
            v-for="product of products"
            v-bind:product="product"
        />
    </div>
</template>

<script>
import ProductItem from '@/components/ProductItem'
export default {
    props: ['products'],
    components: {
        ProductItem
    },
}
</script>