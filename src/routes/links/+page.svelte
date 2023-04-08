<script lang="ts">
	let timesClicked = 0;

	function increment() {
		timesClicked += 1;
	}
</script>

<div class="container">
	<div>
		<h1>Links utilizados para a apresentação</h1>
		<ul>
			<li>
				<a
					href="https://www.w3.org/WAI/fundamentals/accessibility-principles/"
					target="_blank"
					rel="noopener noreferrer"
				>
					W3
				</a>
			</li>
			<li>
				<a
					href="https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA"
					target="_blank"
					rel="noopener noreferrer"
				>
					Mozilla ARIA
				</a>
			</li>
			<li>
				<a
					href="https://github.com/jsx-eslint/eslint-plugin-jsx-a11y/tree/main/docs/rules"
					target="_blank"
					rel="noopener noreferrer"
				>
					Eslint Plugin para acessibilidade
				</a>
			</li>
		</ul>
	</div>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		gap: 0.5rem;
	}

	div {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	li {
		font-size: 1.125rem;
	}

	h1 {
		font-size: 2rem;
	}
</style>
