<script setup>
defineProps({
    totalCost: Number,
    totalCalories: Number,
});
</script>

<template>
    <div class="totals">
        <h2>Totals</h2>
        <p>Total Cost: ${{ totalCost.toFixed(2) }}</p>
        <p>Total Calories: {{ totalCalories }}</p>
    </div>
</template>