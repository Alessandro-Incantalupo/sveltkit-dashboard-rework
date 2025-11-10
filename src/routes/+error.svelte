<script lang="ts">
	import { page } from '$app/state';
	import Icon from '@iconify/svelte';
</script>

<div class="flex min-h-screen items-center justify-center">
	<div class="text-center">
		<h1 class="mb-2">{page.status}: {page.error?.message}</h1>
		<p class="text-gray mb-4">The resource you're looking for doesn't exist or has been removed.</p>
		<a
			href="/resources"
			class="inline-flex items-center gap-2 rounded-lg bg-orange-500 px-4 py-2 text-white hover:bg-orange-600"
		>
			<Icon icon="mdi:arrow-left" class="h-4 w-4" />
			Back to Resources
		</a>
	</div>
</div>
