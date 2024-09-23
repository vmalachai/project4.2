<script setup>
defineProps({
    recipes: Array
});

const handleDelete = (id) => {
    emit('recipeDeleted', id);
};
</script>

<template>
    <div>
        <h2>Recipes</h2>
        <ul>
            <li v-for="recipe in recipes" :key="recipe.id">
                {{ recipe.name }}
                <button @click="handleDelete(recipe.id)">Delete</button>
            </li>
        </ul>
    </div>
</template>
