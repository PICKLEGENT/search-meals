<template>
	<nav
		class="absolute lg:relative top-0 flex flex-col lg:flex-row lg:justify-end lg:items-center lg:gap-x-8 text-2xl lg:text-3xl bg-white duration-500 ease-in-out rounded-l-xl lg:rounded-none shadow-xl lg:shadow-none"
		:class="[
			props.open.value
				? 'right-0 h-screen lg:h-auto'
				: 'right-[-100%] h-screen lg:h-auto',
		]"
	>
		<router-link
			:to="{ name: 'home' }"
			@click="props.openMenu()"
			class="lg:hidden mt-10 px-4 lg:px-3 py-2 text-red-600 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
		>
			Home
		</router-link>
		<router-link
			:to="{ name: 'byName' }"
			@click="props.openMenu()"
			class="px-4 lg:px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
		>
			Search Meals
		</router-link>
		<router-link
			:to="{ name: 'byLetter' }"
			@click="props.openMenu()"
			class="px-4 lg:px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
		>
			Meals By Letter
		</router-link>
		<router-link
			:to="{ name: 'ingredients' }"
			@click="props.openMenu()"
			class="px-4 lg:px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
		>
			Meals By Ingredients
		</router-link>
	</nav>
</template>

<script setup>
const props = defineProps({
	open: Object,
	openMenu: Function,
});
</script>
