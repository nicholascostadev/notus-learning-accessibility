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
	<p aria-hidden="true">Tenta com o teclado</p>
	{#if timesClicked > 0}
		YAY :)
	{/if}
	<div class="box" on:click={increment} on:keydown={handleKeyDown} tabindex="0" />

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
</style>
