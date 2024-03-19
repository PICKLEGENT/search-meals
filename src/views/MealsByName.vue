<template>
	<div class="p-8 pb-0">
		<input
			type="text"
			v-model="keyword"
			class="rounded border-2 border-gray-200 w-full"
			placeholder="Search for Meals"
			@change="searchMeals"
		/>
	</div>
	<div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
		<div
			v-for="meal of meals"
			:key="meal.idMeal"
			class="bg-white shadow rounded-lx"
		>
			<router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
				<img
					:src="meal.strMealThumb"
					:alt="strMeal"
					class="w-full h-48 object-cover rounded-t-lx"
				/>
				<div>
					<h3 class="font-semibold">{{ meal.strMeal }}</h3>
					<p>
						Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quasi
						minima unde perspiciatis eius impedit harum architecto dolorum?
						Velit porro unde libero, asperiores magnam
					</p>
					<div class="flex justify-between items-center">
						<router-link
							to="/"
							class="px-3 py-2 text-white rounded border-2 border-purple-600 bg-purple-500 hover:bg-purple-500 transition-colors"
							>View</router-link
						>
					</div>
				</div>
			</router-link>
		</div>
	</div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
	if (keyword.value) {
		store.dispatch('searchMeals', keyword.value);
	} else {
		store.commit('setSearchedMeals', []);
	}
}

onMounted(() => {
	keyword.value = route.params.name;

	if (keyword.value) {
		searchMeals();
	}
});
</script>
