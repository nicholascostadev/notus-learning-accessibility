<div class="container">
	<small aria-hidden="true">aria-label="Lado Esquerdo legal"</small>
	<small aria-hidden="true">aria-label="Lado Direito legal"</small>
	<div aria-label="Lado Esquerdo legal">Lado Esquerdo</div>
	<div aria-label="Lado Direito legal">Lado Direito</div>
	<p>O que o leitor lê: "Lado Esquerdo"</p>
	<p>O que o leitor lê: "Lado Direito"</p>

	<p aria-hidden="true" style="grid-column: 1/-1;padding-top:1rem">
		PS: Note que ele lê os dois conteúdos (Esquerdo e Direito) sem parar, já que não estão divididos
		por nada.
	</p>
</div>

<style>
	.container {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 0.5rem;

		width: 50%;
	}

	.container > div {
		border: 1px solid #eee;
		border-radius: 16px;
		padding: 0.5rem;
		height: 500px;
	}
</style>
