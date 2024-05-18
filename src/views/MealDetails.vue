<template>
	<h1
		class="px-3 py-2 w-fit font-bold text-5xl border-2 border-red-600 rounded-xl"
	>
		{{ meal.strMeal }}
	</h1>
	<div class="flex gap-x-8 mt-12">
		<img
			:src="meal.strMealThumb"
			:alt="meal.strMeal"
			class="max-w-[100%] object-cover"
		/>
		<section>
			<div class="flex justify-between items-center text-xl">
				<div class="flex items-center gap-x-4">
					<h3 class="font-bold text-2xl">Category:</h3>
					{{ meal.strCategory }}
				</div>
				<div class="flex items-center gap-x-4">
					<h3 class="font-bold text-2xl">Area:</h3>
					{{ meal.strArea }}
				</div>
				<div class="flex items-center gap-x-4">
					<h3 class="font-bold text-2xl">Tags:</h3>
					{{ meal.strTags }}
				</div>
			</div>
			<div class="mt-6 leading-relaxed text-lg">
				{{ meal.strInstructions }}
			</div>
			<div class="flex gap-x-8 mt-6">
				<div>
					<h2 class="font-semibold text-3xl">Ingredients</h2>
					<ul class="mt-3 text-xl">
						<template v-for="(el, ind) of new Array(20)">
							<li v-if="meal[`strIngredient${ind + 1}`]">
								{{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}:
							</li>
						</template>
					</ul>
				</div>
				<div>
					<h2 class="font-semibold text-3xl">Measures</h2>
					<ul class="mt-3 text-xl">
						<template v-for="(el, ind) of new Array(20)">
							<li v-if="meal[`strMeasure${ind + 1}`]">
								{{ meal[`strMeasure${ind + 1}`] }}
							</li>
						</template>
					</ul>
				</div>
			</div>
			<div class="flex justify-start items-center gap-x-8 mt-6">
				<YouTubeButton :href="meal.strYoutube" />
				<a
					:href="meal.strSource"
					target="_blank"
					class="text-xl text-indigo-600"
				>
					View Original Source
				</a>
			</div>
		</section>
	</div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';
import YouTubeButton from '../components/YouTubeButton.vue';

const route = useRoute();
const meal = ref({});

onMounted(() => {
	axiosClient.get(`lookup.php?i=${route.params.id}`).then(({ data }) => {
		meal.value = data.meals[0] || {};
	});
});
</script>
