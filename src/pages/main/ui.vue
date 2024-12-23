<script setup lang="ts">
import { onMounted } from 'vue';
import { Content } from '@/shared/content';
import { ProductsList } from '@/widgets/products-list';
import { useAllProductsStore } from '@/app/stores/allProducts';
import { useCategoriesStore } from '@/app/stores/categories';
import { CategoriesList } from '@/widgets/categories-list';

const storeAllProducts = useAllProductsStore();
const storeCategories = useCategoriesStore();

onMounted(() => {
  storeAllProducts.loadProducts('public_RiNvjTVVzKLhFNWyzR5fNY68u1GMHLEs');
  storeCategories.loadCategories('public_RiNvjTVVzKLhFNWyzR5fNY68u1GMHLEs')
});

const productsData = {
  title: 'All products',
  items: storeAllProducts.products
};

const categoriesData = {
  title: 'All categories',
  items: storeCategories.categories
}

</script>

<template>
    <Content>
      <CategoriesList :data="categoriesData" />
      <ProductsList :data="productsData" />
    </Content>
</template>
