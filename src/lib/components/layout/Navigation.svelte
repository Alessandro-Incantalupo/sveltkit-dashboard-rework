<script lang="ts">
	import { page } from '$app/state';
	import * as Avatar from '$lib/components/ui/avatar/index.js';
	import { navItems } from '$lib/config/navigation/const';
	import Icon from '@iconify/svelte';

	const currentPath = $derived(page.url.pathname);
	let isMobileMenuOpen = $state(false);

	// function isActive(href: string): boolean {
	// 	return currentPath === href;
	// }
	const isActive = (href: string) => {
		return currentPath === href;
	};
</script>

<nav class="bg-nav border-b">
	<!-- Desktop Navigation -->
	<div class="hidden items-center justify-around px-4 md:flex">
		<!-- Logo Section -->
		<div class="flex items-center">
			<div>
				<img
					src="https://cdn.prod.website-files.com/67c5a68d264bc80704ead812/67c5aad643501555a060099a_Pack_logo%20b.png"
					alt="Pack Logo"
					class="h-8"
				/>
			</div>
		</div>

		<!-- Links Section -->
		<div class="flex space-x-4">
			{#each navItems as item}
				{@const active = isActive(item.href)}
				<div class="flex h-full items-center">
					<a
						href={item.href}
						class="border-b-4 px-4 py-4 transition-colors"
						class:text-brand={active}
						class:font-medium={active}
						class:border-brand={active}
						class:border-transparent={!active}
					>
						{item.label}
					</a>
				</div>
			{/each}
		</div>

		<!-- User Section -->
		<div class="flex items-center space-x-4">
			<!-- Country Flag -->
			<div class="h-5 w-11">
				<Icon icon="flagpack:us" class="text-blue h-full w-full rounded-lg" />
			</div>

			<!-- User Avatar -->
			<div
				class="bg-gray-light border-pack flex h-8 w-8 items-center justify-center overflow-hidden rounded-full border-2"
			>
				<Avatar.Root>
					<Avatar.Image src="https://github.com/shadcn.png" alt="@shadcn" />
					<Avatar.Fallback>CN</Avatar.Fallback>
				</Avatar.Root>
			</div>
		</div>
	</div>

	<!-- Mobile Navigation -->
	<div class="md:hidden">
		<!-- Mobile Header -->
		<div class="flex items-center justify-between px-4 py-3">
			<!-- Hamburger Menu Button -->
			<button
				onclick={() => (isMobileMenuOpen = !isMobileMenuOpen)}
				class="rounded-md p-2 hover:bg-muted focus:ring-2 focus:ring-brand focus:outline-none"
				aria-label="Toggle navigation menu"
			>
				<Icon icon={isMobileMenuOpen ? 'lucide:x' : 'lucide:menu'} class="h-6 w-6" />
			</button>

			<!-- Centered Logo -->
			<div class="flex items-center">
				<img
					src="https://cdn.prod.website-files.com/67c5a68d264bc80704ead812/67c5aad643501555a060099a_Pack_logo%20b.png"
					alt="Pack Logo"
					class="h-8"
				/>
			</div>

			<!-- User Avatar -->
			<div
				class="bg-grey-light border-pack flex h-8 w-8 items-center justify-center overflow-hidden rounded-full border-2"
			>
				<Avatar.Root>
					<Avatar.Image src="https://github.com/shadcn.png" alt="@shadcn" />
					<Avatar.Fallback>CN</Avatar.Fallback>
				</Avatar.Root>
			</div>
		</div>

		<!-- Mobile Menu -->
		{#if isMobileMenuOpen}
			<div class="border-t bg-muted/50 px-4 py-2 transition-all duration-200" role="menu">
				{#each navItems as item}
					{@const active = isActive(item.href)}
					<a
						href={item.href}
						onclick={() => (isMobileMenuOpen = false)}
						class="block rounded-md px-4 py-3 transition-colors hover:bg-muted"
						class:text-brand={active}
						class:font-medium={active}
						role="menuitem"
					>
						{item.label}
					</a>
				{/each}

				<!-- Mobile User Info -->
				<div class="mt-4 flex items-center justify-between border-t pt-4">
					<span class="text-sm text-muted-foreground">Logged in as</span>
					<div class="flex items-center space-x-2">
						<div class="h-4 w-8">
							<Icon icon="flagpack:us" class="h-full w-full rounded" />
						</div>
						<span class="text-sm">User</span>
					</div>
				</div>
			</div>
		{/if}
	</div>
</nav>
