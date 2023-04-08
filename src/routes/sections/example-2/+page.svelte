<div class="container">
	<small aria-hidden="true">aria-label="Lado Esquerdo legal"</small>
	<small aria-hidden="true">aria-label="Lado Direito legal"</small>
	<section aria-label="Lado Esquerdo legal">Lado Esquerdo</section>
	<section aria-label="Lado Direito legal">Lado Direito</section>
	<p>O que o leitor lê: "Lado Esquerdo legal 'região' Lado Esquerdo"</p>
	<p>O que o leitor lê: "Lado Direito legal 'região' Lado Esquerdo"</p>

	<p aria-hidden="true" style="grid-column: 1/-1;padding-top:1rem">
		PS: Note que assim que focamos no lado esquerdo, ele lê apenas o conteúdo do lado esquerdo,
		focando na "região" selecionada.
	</p>
</div>

<style>
	.container {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 0.5rem;

		width: 50%;
	}

	.container > section {
		border: 1px solid #eee;
		border-radius: 16px;
		padding: 0.5rem;
		height: 500px;
	}
</style>
