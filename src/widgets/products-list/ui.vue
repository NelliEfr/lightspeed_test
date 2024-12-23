<script lang="ts" setup>
import { ProductCard } from '@/entities/product/card';
import { type Product } from '@/entities/product/model/types';
import { Typography } from '@/shared/typograghy';

interface CardsProps {
  data: {
    title: string;
    items: Product[];
  }
}

const { data } = defineProps<CardsProps>();

</script>

<template>
    <section class="products-list">
        <Typography tagName="h2">{{ data.title }}</Typography>
        <div v-if="data.items.length" class="products-list__container">
            <ProductCard v-for="product in data.items" :key="product.id" :data="product" />
        </div>
        <Typography tagName="p" v-else>Products are loading...</Typography>
    </section>
</template>

<style scoped>
.products-list {
  display: flex;
  flex-direction: column;
  gap: 40px;
  padding: 30px 0;
}

.products-list__container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  row-gap: 20px;
  column-gap: 30px;
}

@media screen and (max-width: 768px){
    .products-list__container {
      grid-template-columns: 1fr;
    }
}
</style>