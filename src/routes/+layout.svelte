<script lang="ts">
	import '../app.css';
	import { page } from '$app/stores';

	let lastPressedKey = '';
	let timesPressedSameKey = 0;

	function handleKeyDown(event: KeyboardEvent) {
		if (event.key === lastPressedKey) {
			timesPressedSameKey += 1;
		} else {
			timesPressedSameKey = 0;
		}
		lastPressedKey = event.key === ' ' ? 'Space' : event.key;
	}

	$: pageName = $page.url.pathname.split('/')[1];
</script>

<svelte:window on:keydown={handleKeyDown} />
<svelte:head>
	<title>Acessibilidade {pageName !== '' ? `| ${pageName}` : ''}</title>
</svelte:head>
<nav>
	<a href="/">Home</a>
	<div class="first-part">
		<h2>Div</h2>
		<ul>
			<li>
				<a href="/div/example-1">Part 1</a>
			</li>
			<li>
				<a href="/div/example-2">Part 2</a>
			</li>
			<li>
				<a href="/div/example-3">Part 3</a>
			</li>
			<li>
				<a href="/div/example-4">Part 4</a>
			</li>
		</ul>
	</div>

	<div class="first-part">
		<h2>Aria</h2>
		<ul>
			<li>
				<a href="/aria/example-1">Part 1</a>
			</li>
			<li>
				<a href="/aria/example-2">Part 2</a>
			</li>
		</ul>
	</div>

	<div class="first-part">
		<h2>Sections</h2>
		<ul>
			<li>
				<a href="/sections/example-1">Part 1</a>
			</li>
			<li>
				<a href="/sections/example-2">Part 2</a>
			</li>
		</ul>
	</div>
</nav>
<main>
	<slot />
</main>

<aside class="key-info" aria-hidden="true">
	{#if timesPressedSameKey > 0}
		<p aria-hidden="true">{timesPressedSameKey}</p>
	{/if}
	<p aria-hidden="true">{lastPressedKey}</p>
</aside>

<style>
	:root {
		--nav-height: 100px;
	}

	nav {
		background-color: #0d0d0d;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 1rem;

		height: var(--nav-height);

		font-size: 1.25rem;
	}

	nav > a {
		cursor: pointer;
	}

	ul {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;

		font-size: 1.25rem;
		list-style: none;
	}

	main {
		height: calc(100vh - var(--nav-height));
		background-color: #0d0d0d;

		display: flex;
		align-items: center;
		justify-content: center;

		font-size: 1.25rem;
	}

	.key-info {
		position: fixed;
		bottom: 16px;
		right: 16px;
		padding: 0.5rem;
		background-color: #0d0d0d;

		color: #fff;
		font-size: 2rem;
		text-align: right;
	}

	h2 {
		font-size: 1.5rem;
	}

	.first-part {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;

		border: 1px solid #fdfdfd;
		border-radius: 8px;
		padding: 0.5rem;
	}
</style>
