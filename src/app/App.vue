<script setup lang="ts">
import { Header } from '@/widgets/header';
import { RouterView } from 'vue-router';
import { useAllProductsStore } from './stores/allProducts';
import { useCategoriesStore } from './stores/categories';
import { onMounted } from 'vue';

const storeAllProducts = useAllProductsStore();
const storeCategories = useCategoriesStore();

</script>

<template>
  <Header />
  <RouterView />
</template>

<style scoped>

</style>
