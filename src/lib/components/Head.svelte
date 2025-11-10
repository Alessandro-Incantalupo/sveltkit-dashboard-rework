<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	let {
		title = 'Dashboard',
		description = 'A modern SvelteKit dashboard application',
		author = 'Alessandro Incantalupo',
		keywords = 'svelte, sveltekit, dashboard'
	} = $props();
</script>

<svelte:head>
	<!-- Favicon -->
	<link rel="icon" href={favicon} />

	<!-- Meta Tags -->
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<meta name="description" content={description} />
	<meta name="author" content={author} />
	<meta name="keywords" content={keywords} />

	<!-- Open Graph / Facebook -->
	<meta property="og:type" content="website" />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />

	<!-- Twitter -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />

	<!-- Title -->
	<title>{title}</title>
</svelte:head>
