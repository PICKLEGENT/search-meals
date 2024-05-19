<template>
	<div class="grid grid-cols-1 lg:grid-cols-4 gap-6 mt-6 lg:mt-12">
		<MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
	</div>
	<div
		v-if="!meals.length"
		class="mt-12 lg:mt-24 text-center text-4xl text-gray-600"
	>
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
