<template>
	<h1
		class="px-3 py-2 w-full lg:w-fit text-center text-2xl lg:text-5xl border-2 border-red-600 rounded-xl"
	>
		Meals by Letter
	</h1>
	<div
		class="grid grid-cols-4 lg:flex justify-center mt-6 lg:mt-12 gap-12 lg:gap-x-8"
	>
		<router-link
			:to="{ name: 'byLetter', params: { letter } }"
			v-for="letter of letters"
			:key="letter"
			class="text-center text-4xl hover:text-red-600 hover:scale-150 transition-all"
		>
			{{ letter }}
		</router-link>
	</div>

	<Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';

const route = useRoute();
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const meals = computed(() => store.state.mealsByLetter);

watch(route, () => {
	store.dispatch('searchMealsByLetter', route.params.letter);
});

onMounted(() => {
	store.dispatch('searchMealsByLetter', route.params.letter);
});
</script>
