<script setup>
import Header from './components/Head.vue';
import Totals from './components/Totals.vue';
import RecipeList from './components/RecipeList.vue';
import AddRecipe from './components/AddRecipe.vue';

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

const handleAddRecipe = (recipeData) => {
    recipes.value.push({
        id: generateID(),
        name: recipeData.name,
        ingredients: recipeData.ingredients,
        totalCost: recipeData.totalCost,
        totalCalories: recipeData.totalCalories,
    });
    saveToLocalStorage();
};

const handleDeleteRecipe = (id) => {
    recipes.value = recipes.value.filter((recipe) => recipe.id !== id);
    saveToLocalStorage();
};

const generateID = () => {
    return Math.floor(Math.random() * 1000000);
};

const saveToLocalStorage = () => {
    localStorage.setItem('recipes', JSON.stringify(recipes.value));
};

onMounted(() => {
    const savedRecipes = JSON.parse(localStorage.getItem('recipes'));
    if (savedRecipes) {
        recipes.value = savedRecipes;
    };
  })


</script>

<template>
  <Header></Header>
<div class="container">

<Totals :totalCost="totalCost" :totalCalories="totalCalories"></Totals>
<AddRecipe @recipeSubmitted="handleAddRecipe"></AddRecipe>
<RecipeList :recipes="recipes" @recipeDeleted="handleDeleteRecipe"></RecipeList>
</div>
</template>