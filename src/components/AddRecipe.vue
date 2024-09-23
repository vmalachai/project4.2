<script setup>
import { ref } from 'vue';

const name = ref('');
const ingredients = ref([]);
const totalCost = ref(0);
const totalCalories = ref(0);

const submitRecipe = () => {
    const recipeData = {
        name: name.value,
        ingredients: ingredients.value,
        totalCost: totalCost.value,
        totalCalories: totalCalories.value
    };
    name.value = '';
    ingredients.value = [];
    totalCost.value = 0;
    totalCalories.value = 0;
    emit('recipeSubmitted', recipeData);
};

const addIngredient = (ingredient) => {
    ingredients.value.push(ingredient);
    totalCost.value += ingredient.cost;
    totalCalories.value += ingredient.calories;
};
</script>

<template>
    <div>
        <h2>Add Recipe</h2>
        <input v-model="name" placeholder="Recipe name" />
        <button @click="submitRecipe">Add Recipe</button>
    </div>
</template>