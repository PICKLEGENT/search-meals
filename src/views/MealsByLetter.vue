<template>
	<h1
		class="px-3 py-2 w-fit font-bold text-5xl border-2 border-red-600 rounded-xl"
	>
		Meals by Letter
	</h1>
	<div class="flex flex-wrap justify-center mt-12 gap-x-8 px-8">
		<router-link
			:to="{ name: 'byLetter', params: { letter } }"
			v-for="letter of letters"
			:key="letter"
			class="w-2 h-2 flex items-center justify-center text-5xl hover:text-red-600 hover:scale-150 transition-all"
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
