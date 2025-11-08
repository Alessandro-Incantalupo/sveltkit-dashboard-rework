<script lang="ts">
	import { m } from '$lib/paraglide/messages.js';
	import { getLocale, setLocale } from '$lib/paraglide/runtime';

	let userName = 'Alessandro';
	let productCount = 42;
	let currentLocale = $derived(getLocale());
</script>

<div class="demo-container">
	<h1>{m.hello_world({ name: userName })}</h1>
	<p class="welcome">{m.welcome_message()}</p>

	<div class="language-selector">
		<h2>{m.language_selector()}</h2>
		<div class="button-group">
			<button onclick={() => setLocale('en')} class:active={currentLocale === 'en'}>
				🇬🇧 English
			</button>
			<button onclick={() => setLocale('es')} class:active={currentLocale === 'es'}>
				🇪🇸 Español
			</button>
			<button onclick={() => setLocale('it')} class:active={currentLocale === 'it'}>
				🇮🇹 Italiano
			</button>
		</div>
	</div>

	<p class="product-count">{m.products_count({ count: productCount })}</p>

	<div class="info-box">
		<p>
			<strong>Current locale:</strong>
			{currentLocale}
		</p>
		<p>
			If you use VSCode, install the <a
				href="https://marketplace.visualstudio.com/items?itemName=inlang.vs-code-extension"
				target="_blank">Sherlock i18n extension</a
			> for a better i18n experience with inline translations!
		</p>
	</div>
</div>

<style>
	.demo-container {
		max-width: 800px;
		margin: 2rem auto;
		padding: 2rem;
		font-family:
			system-ui,
			-apple-system,
			sans-serif;
	}

	h1 {
		font-size: 2.5rem;
		margin-bottom: 1rem;
		color: #ff3e00;
	}

	.welcome {
		font-size: 1.2rem;
		color: #666;
		margin-bottom: 2rem;
	}

	.language-selector {
		margin: 2rem 0;
		padding: 1.5rem;
		background: #f5f5f5;
		border-radius: 8px;
	}

	.language-selector h2 {
		font-size: 1.2rem;
		margin-bottom: 1rem;
		color: #333;
	}

	.button-group {
		display: flex;
		gap: 1rem;
		flex-wrap: wrap;
	}

	button {
		padding: 0.75rem 1.5rem;
		font-size: 1rem;
		border: 2px solid #ddd;
		background: white;
		border-radius: 6px;
		cursor: pointer;
		transition: all 0.2s;
	}

	button:hover {
		border-color: #ff3e00;
		background: #fff5f3;
	}

	button.active {
		background: #ff3e00;
		color: white;
		border-color: #ff3e00;
	}

	.product-count {
		font-size: 1.1rem;
		margin: 2rem 0;
		padding: 1rem;
		background: #e8f5e9;
		border-left: 4px solid #4caf50;
		border-radius: 4px;
	}

	.info-box {
		margin-top: 3rem;
		padding: 1rem;
		background: #e3f2fd;
		border-radius: 6px;
		font-size: 0.9rem;
	}

	.info-box p {
		margin: 0.5rem 0;
	}

	.info-box a {
		color: #1976d2;
		text-decoration: underline;
	}

	.info-box a:hover {
		color: #ff3e00;
	}
</style>
