<template>
	<div class="bg-white shadow rounded-xl">
		<router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
			<img
				:src="meal.strMealThumb"
				:alt="meal.strMeal"
				class="w-full h-48 object-cover rounded-t-xl"
			/>
		</router-link>
		<div class="p-3">
			<h3 class="font-semibold">{{ meal.strMeal }}</h3>
			<p>
				Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quasi minima
				unde perspiciatis eius impedit harum architecto dolorum? Velit porro
				unde libero, asperiores magnam
			</p>
		</div>
	</div>
</template>

<script setup>
const { meal } = defineProps({
	meal: {
		require: true,
		type: Object,
	},
});
</script>
