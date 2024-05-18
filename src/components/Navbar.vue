<template>
	<header
		class="flex justify-between items-center px-8 py-4 bg-white shadow-lg tracking-wider"
	>
		<router-link
			:to="{ name: 'home' }"
			class="font-black text-5xl text-red-600"
		>
			AR23 | Receipt App
		</router-link>
		<div class="flex justify-end items-center gap-x-8 font-bold text-3xl">
			<router-link
				:to="{ name: 'byName' }"
				class="px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
			>
				Search Meals
			</router-link>
			<router-link
				:to="{ name: 'byLetter' }"
				class="px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
			>
				Meals By Letter
			</router-link>
			<router-link
				:to="{ name: 'ingredients' }"
				class="px-3 py-2 hover:bg-neutral-100 hover:scale-[1.04] hover:shadow-xl rounded-xl duration-200 ease-in"
			>
				Meals By Ingredients
			</router-link>
		</div>
	</header>
</template>
