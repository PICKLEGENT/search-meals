<template>
	<h1
		class="px-3 py-2 w-full lg:w-fit text-center text-2xl lg:text-5xl border-2 border-red-600 rounded-xl"
	>
		Search Meals
	</h1>
	<div class="flex justify-center items-center mt-12">
		<input
			type="text"
			v-model="keyword"
			class="w-full lg:w-[600px] border-2 border-gray-200 bg-white rounded-xl"
			placeholder="Search for Meals"
			@change="searchMeals"
		/>
	</div>
	<Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';

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
