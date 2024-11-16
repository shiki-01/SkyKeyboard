<script lang="ts">
	import { colorScheme } from '$lib';
	import Icon from '@iconify/svelte';

	let input = '';

	const copyToClipboard = () => {
		navigator.clipboard.writeText(input);
		input = '';
	};
</script>

<main
	class="flex h-[100svh] w-[100svw] flex-col items-center justify-center gap-5"
	style="
        background-color: {colorScheme.background};
        color: {colorScheme.text};
    "
>
	<input
		type="text"
		placeholder="Enter text"
		bind:value={input}
		class="overflow-x-auto rounded-lg border-0 p-4 text-sm shadow-lg"
		style="
            background-color: {colorScheme.backgroundSecondary};
            color: {colorScheme.text};
            shadow-color: {colorScheme.shadow};
        "
	/>
	<button
		class="flex flex-row items-center justify-center gap-5 rounded-lg px-3 py-2 text-sm shadow-lg"
		style="
            background-color: {colorScheme.primary};
            color: {colorScheme.text};
            shadow-color: {colorScheme.shadow};
        "
		on:click={copyToClipboard}
	>
		Copy Text
		<Icon icon="bi:clipboard" class="h-4 w-4" />
	</button>
</main>
