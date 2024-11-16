<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	import { browser } from '$app/environment';

	let { children } = $props();

	onMount(() => {
		if (typeof window === 'undefined') return;
		window.addEventListener('touchmove', (e) => e.preventDefault(), { passive: false });
		if (browser && 'serviceWorker' in navigator) {
			navigator.serviceWorker.register('/service-worker.js');
		}
	});
</script>

<svelte:head>
	<title>Sky Keyboard</title>
	<meta
		name="viewport"
		content="width=device-width, initial-scale=1.0 maximum-scale=1.0, user-scalable=no"
	/>
</svelte:head>

{@render children()}

<style>
	:global(*) {
		touch-action: none;
	}

	:global(html),
	:global(body) {
		margin: 0;
		padding: 0;
		overflow: hidden;
	}
</style>
