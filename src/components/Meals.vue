<template>
	<div class="grid grid-cols-1 md:grid-cols-4 gap-5 mt-12">
		<MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
	</div>
	<div v-if="!meals.length" class="mt-24 text-center text-4xl text-gray-600">
		There are no meals
	</div>
</template>

<script setup>
import MealItem from './MealItem.vue';

const { meals } = defineProps({
	meals: {
		required: true,
		type: Array,
	},
});
</script>
