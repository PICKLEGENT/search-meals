<template>
	<header
		class="hidden lg:flex justify-between items-center px-4 lg:px-8 py-4 tracking-wider bg-white shadow-lg rounded-b-xl"
	>
		<div class="flex justify-between items-center relative">
			<router-link
				:to="{ name: 'home' }"
				class="font-bold text-2xl lg:text-5xl text-red-600"
			>
				AR23 | Recipes App
			</router-link>
		</div>
		<navbar v-bind="props" />
	</header>
	<header class="lg:hidden relative h-10">
		<button
			@click="openMenu()"
			class="menu absolute right-3 flex lg:hidden z-10"
			:class="[open ? 'opened' : null]"
		>
			<svg width="50" height="50" viewBox="0 0 100 100">
				<path
					class="line line1"
					d="M 20,29.000046 H 80.000231 C 80.000231,29.000046 94.498839,28.817352 94.532987,66.711331 94.543142,77.980673 90.966081,81.670246 85.259173,81.668997 79.552261,81.667751 75.000211,74.999942 75.000211,74.999942 L 25.000021,25.000058"
				/>
				<path class="line line2" d="M 20,50 H 80" />
				<path
					class="line line3"
					d="M 20,70.999954 H 80.000231 C 80.000231,70.999954 94.498839,71.182648 94.532987,33.288669 94.543142,22.019327 90.966081,18.329754 85.259173,18.331003 79.552261,18.332249 75.000211,25.000058 75.000211,25.000058 L 25.000021,74.999942"
				/>
			</svg>
		</button>
		<navbar v-bind="props" />
	</header>
</template>

<script setup>
import { ref } from 'vue';
import Navbar from '../components/Navbar.vue';

const width = window.innerWidth;

let open;
let status;

if (width <= 1024) {
	open = ref(false);
} else {
	open = ref(true);
}

const openMenu = () => {
	if (width <= 1024) {
		open.value = !open.value;
	} else {
		open.value = true;
	}
	status = open.value;
};

let props = {
	open,
	openMenu,
};
</script>
