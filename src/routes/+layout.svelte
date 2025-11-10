<script lang="ts">
	import Head from '$lib/components/Head.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Head />

<main>
	{@render children()}
</main>
