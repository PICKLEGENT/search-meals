<template>
	<h1
		class="px-3 py-2 w-full lg:w-fit text-center text-2xl lg:text-5xl border-2 border-red-600 rounded-xl"
	>
		You might like it
	</h1>
	<Meals :meals="meals" />
</template>

<script setup>
import { onMounted, ref } from 'vue';
import Meals from '../components/Meals.vue';
import axiosClient from '../axiosClient.js';

const meals = ref([]);

onMounted(async () => {
	for (let i = 0; i < 10; i++) {
		axiosClient
			.get(`random.php`)
			.then(({ data }) => meals.value.push(data.meals[0]));
	}
});
</script>
