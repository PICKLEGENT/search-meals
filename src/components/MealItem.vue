<template>
	<div
		class="bg-neutral-100 rounded-xl shadow hover:scale-105 transition-all overflow-hidden"
	>
		<router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
			<img
				:src="meal.strMealThumb"
				:alt="meal.strMeal"
				class="w-full h-48 object-cover"
			/>
		</router-link>
		<div class="p-3">
			<h3 class="text-2xl">{{ meal.strMeal }}</h3>
			<p v-if="meal.strInstructions" class="mt-3 text-xl">
				{{ $filters.truncateWords(meal.strInstructions, 20) }}
			</p>
		</div>
	</div>
</template>

<script setup>
const { meal } = defineProps({
	meal: {
		required: true,
		type: Object,
	},
});
</script>
