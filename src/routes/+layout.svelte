<script>
	import '../app.css';
	let lastPressedKey = '';
</script>

<svelte:window on:keydown={(e) => (lastPressedKey = e.key)} />
<nav>
	<a href="/">Home</a>
	<ul>
		<li>
			<a href="/exemplo-1">Part 1</a>
		</li>
		<li>
			<a href="/exemplo-2">Part 2</a>
		</li>
		<li>
			<a href="/exemplo-3">Part 3</a>
		</li>
		<li>
			<a href="/exemplo-4">Part 4</a>
		</li>
	</ul>

	<ul>
		<li>
			<a href="/exemplo-5">Part 5</a>
		</li>
		<li>
			<a href="/exemplo-6">Part 6</a>
		</li>
	</ul>
</nav>
<main>
	<slot />
</main>

<aside class="key-info">
	<p>{lastPressedKey}</p>
</aside>

<style>
	:root {
		--nav-height: 50px;
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
		position: absolute;
		bottom: 16px;
		right: 16px;
		padding: 0.5rem;
		background-color: #0d0d0d;
		color: #fff;

		font-size: 2rem;
	}
</style>
