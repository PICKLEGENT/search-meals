<template>
	<navbar />
	<main>
		<div class="p-8 tracking-wider">
			<router-view />
		</div>
	</main>
</template>

<script setup>
import Navbar from '../components/Navbar.vue';
</script>
