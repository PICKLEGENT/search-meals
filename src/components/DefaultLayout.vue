<template>
	<Header />
	<main>
		<div class="p-4 lg:p-8 tracking-wider">
			<router-view />
		</div>
	</main>
</template>

<script setup>
import Header from '../components/Header.vue';
</script>
