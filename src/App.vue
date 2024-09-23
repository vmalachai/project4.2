<script setup>
import Header from './components/Head.vue';
import Totals from './components/Totals.vue';

const recipes = ref([]);

const totalCost = computed(() => {
    return recipes.value.reduce((acc, recipe) => {
        return acc + recipe.totalCost;
    }, 0);
});

const totalCalories = computed(() => {
    return recipes.value.reduce((acc, recipe) => {
        return acc + recipe.totalCalories;
    }, 0);
});


</script>

<template>
  <Header></Header>
<div class="container">

<Totals :totalCost="totalCost" :totalCalories="totalCalories"></Totals>

</div>
</template>