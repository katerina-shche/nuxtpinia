<template>
    <div>
        <h2 class="text-white text-2xl text-center my-8">Your Basket</h2>
        <div v-if="cartStore.cart.length">
        <!-- product list -->
            <div v-for="product in cartStore.cart" class="flex gap-8 items-center">
                <img :src="product.img" :alt="product.title">
                <p class="text-white">{{ product.title }}</p>
                <!-- product quantity -->
                <ProductQuantity :product="product"/>
                <p class="text-white">{{ product.price * product.quantity }} coins.</p>

                <!-- delete -->
                <button class="ml-auto" @click="cartStore.deleteFromCart(product)">
                    <span class="material-symbols-outlined text-white">Delete</span>
                </button>
            </div>
        <!-- cart total -->
            <div class="text-right pt-4 mt-4 border-t-2">
                <span class="text-white">Total amount to pay: </span>
                <span class="text-secondary">{{ cartStore.cartTotal }} coins.</span>
            </div>
        </div>
        <div v-else>
            <p class="text-white">There are no items in your basket.</p>
        </div>
    </div>
</template>

<script setup>
    import { useCartStore } from '@/stores/cartStore'

    const cartStore = useCartStore()



</script>

<style scoped>

</style>