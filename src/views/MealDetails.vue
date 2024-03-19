<template>
	<div class="w-[800px] mx-auto p-8">
		<h1 class="font-bold text-5xl mb-5">{{ meal.srtMeal }}</h1>
		<img :src="meal.srtMealThumb" :alt="meal.srtMeal" />
		<div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
			<div><strong>Category:</strong> {{ meal.srtCategory }}</div>
			<div><strong>Area:</strong> {{ meal.srtArea }}</div>
			<div><strong>Tags:</strong> {{ meal.srtTags }}</div>
		</div>
		<div class="grid grid-cols-1 sm:grid-cols-2">
			<div>
				<h2 class="mb-2 font-semibold text-2xl">Ingredients</h2>
				<ul>
					<template v-for="(el, index) of new Array(20)">
						<li v-if="meal[`strIngredient${index + 1}`]">
							{{ index + 1 }}. {{ meal[`strIngredient${index + 1}`] }}
						</li>
					</template>
				</ul>
			</div>
			<div>
				<h2 class="mb-3 font-semibold text-2xl">Measures</h2>
				<ul>
					<template v-for="(el, index) of new Array(20)">
						<li v-if="meal[`strMeasures${index + 1}`]">
							{{ index + 1 }}. {{ meal[`strMeasures${index + 1}`] }}
						</li>
					</template>
				</ul>
			</div>
		</div>
	</div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const meal = ref({});

onMounted(() => {
	axiosClient.get(`lookup.php?i=${route.parms.id}`).then(({ data }) => {
		meal.value = data.meals[0] || {};
	});
	a;
});
</script>
