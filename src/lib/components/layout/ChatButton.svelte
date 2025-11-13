<script lang="ts">
	import Icon from '@iconify/svelte';
	import { toast } from 'svelte-sonner';

	function toggleChat() {
		toast.info(`"Work in progress"`, {
			description: 'This feature will be available soon!',
			duration: 3000
		});
	}
</script>

<!-- Chat Button -->
<button
	class="fixed right-6 bottom-6 z-50 flex h-14 w-14 items-center justify-center rounded-full bg-brand text-white shadow-lg transition-colors duration-200 hover:bg-brand-dark"
	onclick={toggleChat}
	aria-label="Open chat"
>
	<Icon icon="tdesign:chat-double" class="h-6 w-6" />
	<!-- Green Circle Badge -->
	<span class="absolute bottom-1 left-10 h-4 w-4 rounded-full border-2 border-white bg-green"
	></span>
</button>
