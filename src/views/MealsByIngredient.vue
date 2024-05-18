<template>
	<h1
		class="px-3 py-2 w-fit font-bold text-5xl border-2 border-red-600 rounded-xl"
	>
		Meals for {{ ingredient.strIngredient }}
	</h1>
	<Meals :meals="meals" />
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import Meals from '../components/Meals.vue';

const route = useRoute();
const ingredient = computed(() => store.state.ingredient);
const meals = computed(() => store.state.mealsByIngredient);

onMounted(() => {
	store.dispatch('searchMealsByIngredient', route.params.ingredient);
});
</script>
