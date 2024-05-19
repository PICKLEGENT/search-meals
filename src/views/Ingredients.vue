<template>
	<div>
		<h1
			class="px-3 py-2 w-full lg:w-fit text-center text-2xl lg:text-5xl border-2 border-red-600 rounded-xl"
		>
			Ingredients
		</h1>
	</div>
	<div class="mt-6">
		<div class="flex justify-center items-center">
			<input
				type="text"
				v-model="keyword"
				class="w-full lg:w-[600px] border-2 border-gray-200 bg-white rounded-xl"
				placeholder="Search for Ingredients"
			/>
		</div>
		<div class="mt-6 lg:mt-12 grid grid-cols-2 lg:grid-cols-4 gap-4">
			<a
				href="#"
				@click.prevent="openIngredient(ingredient)"
				v-for="ingredient of computedIngredients"
				:key="ingredient.idIngredient"
				class="block p-2 text-xl lg:text-3xl bg-neutral-100 hover:text-red-600 transition-colors rounded-xl shadow"
			>
				{{ ingredient.strIngredient }}
			</a>
		</div>
	</div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';
import axiosClient from '../axiosClient';
import store from '../store';

const router = useRouter();
const keyword = ref('');
const ingredients = ref([]);
const computedIngredients = computed(() => {
	if (!computedIngredients) return ingredients;
	return ingredients.value.filter((i) =>
		i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
	);
});

function openIngredient(ingredient) {
	store.commit('setIngredient', ingredient);
	router.push({
		name: 'byIngredient',
		params: { ingredient: ingredient.strIngredient },
	});
}

onMounted(() => {
	axiosClient.get('list.php?i=list').then(({ data }) => {
		ingredients.value = data.meals;
	});
});
</script>
