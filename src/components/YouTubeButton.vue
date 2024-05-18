<template>
	<a
		:href="href"
		target="_blank"
		class="px-3 py-2 text-xl text-white border-2 border-[#FF0000] bg-[#FF0000] hover:border-[#282828] rounded-xl duration-200 ease-in"
	>
		<slot>YouTube</slot>
	</a>
</template>

<script setup>
const props = defineProps({
	href: String,
});
</script>
