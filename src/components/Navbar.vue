<template>
	<nav
		class="absolute lg:relative top-0 flex flex-col lg:flex-row lg:justify-end lg:items-center lg:gap-x-8 text-2xl lg:text-3xl bg-white duration-500 ease-in-out rounded-l-xl lg:rounded-none shadow-xl lg:shadow-none"
		:class="[
			props.open.value
				? 'flex flex-col justify-between right-0 h-screen lg:h-auto'
				: 'flex flex-col justify-between right-[-100%] h-screen lg:h-auto',
		]"
	>
		<div class="flex flex-col lg:flex-row">
			<router-link
				:to="{ name: 'home' }"
				@click="props.openMenu()"
				class="lg:hidden mt-16 px-4 lg:px-3 py-2 text-red-600 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
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
		</div>
		<div class="lg:hidden">
			<div class="flex justify-center items-center gap-x-8 mt-3">
				<a
					href="https://github.com/PICKLEGENT"
					target="_blanc"
					class="text-lg lg:text-2xl"
					>GitHub</a
				>
				<a
					href="https://t.me/AndrewRom"
					target="_blanc"
					class="text-lg lg:text-2xl"
					>Telegram</a
				>
			</div>
			<p
				class="mt-6 text-center text-sm lg:text-base text-gray-500 leading-relaxed"
			>
				Code by<br />Andrew Romanov
			</p>
		</div>
	</nav>
</template>

<script setup>
const props = defineProps({
	open: Object,
	openMenu: Function,
});
</script>
