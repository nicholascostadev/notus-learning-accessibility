<script lang="ts">
	let timesClicked = 0;

	function increment() {
		timesClicked += 1;
	}

	function handleKeyDown(event: KeyboardEvent) {
		if (event.key !== 'Enter') return;

		increment();
	}
</script>

<div class="container">
	<div class="box" on:click={increment} on:keydown={handleKeyDown} tabindex="0" role="button">
		<span class="sr-only">Botão que incrementa a contagem</span>
	</div>

	<p>Clicked {timesClicked} times</p>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		gap: 0.5rem;
	}

	.box {
		height: 50px;
		width: 50px;
		background-color: steelblue;
	}

	.sr-only {
		position: absolute;
		width: 1px;
		height: 1px;
		padding: 0;
		margin: -1px;
		overflow: hidden;
		clip: rect(0, 0, 0, 0);
		white-space: nowrap;
		border-width: 0;
	}
</style>
