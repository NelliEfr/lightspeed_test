<script lang="ts" setup>
import { computed, reactive } from 'vue';
import { Wrapper } from '@/shared/wrapper';
import { Navigation } from '@/features/navigation';
import { AkShoppingBag } from '@kalimahapps/vue-icons';
import { AkHeart } from '@kalimahapps/vue-icons';
import { useShoppingCartStore } from '@/app/stores/shoppingCart';

const storeShoppingCart = useShoppingCartStore();
const cartProductsCount = computed(() => storeShoppingCart.cartProducts.reduce((acc, el) => acc + el.count, 0));


const navItems = reactive([
    { label: 'Main page', link: '/', fontSize: 'l' },
    // { label: 'Favorites', link: '/favorites', fontSize: 's', icon: AkHeart, count: 0 },
    { label: 'Cart', link: '/cart', fontSize: 's', icon: AkShoppingBag, count: cartProductsCount }
])
</script>

<template>
    <header class="header">
        <Wrapper>
            <Navigation :data="navItems" />
        </Wrapper>
    </header>
</template>

<style scoped>
.header {
    border-bottom: 2px solid var(--grayscale-hardest);
    padding: 10px 0;
}
</style>