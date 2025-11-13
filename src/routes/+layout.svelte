<script lang="ts">
	import Head from '$lib/components/Head.svelte';
	import ChatButton from '$lib/components/layout/ChatButton.svelte';
	import Navigation from '$lib/components/layout/Navigation.svelte';
	import { Toaster } from 'svelte-sonner';
	import '../app.css';

	let { children } = $props();
</script>

<Head />
<Navigation />

<main class="mx-auto">
	{@render children()}
</main>

<ChatButton />
<Toaster richColors />
