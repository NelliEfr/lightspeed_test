<script lang="ts" setup>
import { type Category } from '@/entities/category/model/types';
import { Typography } from '@/shared/typograghy';
import { CategoryCard } from '@/entities/category/card';

interface CardsProps {
    data: {
        title: string,
        items: Category[]
    }
}

const { data } = defineProps<CardsProps>();
const { 
  title = "N/A",
  items,
} = data;

</script>

<template>
    <section class="categories-list">
        <Typography tagName="h2" bold>{{ title }}</Typography>
        <div v-if="items.length" class="categories-list__container">
            <CategoryCard v-for="category in items" :key="category.id" :data="category" />
        </div>
        <p v-else>Categories are loading...</p>
    </section>
</template>

<style scoped>
.categories-list {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding: 30px 0;
}

.categories-list__container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
}

@media screen and (max-width: 768px){
    .categories-list__container {
        grid-template-columns: 1fr;
        gap: 20px;
    }
}
</style>