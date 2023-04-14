<script lang="ts">
	import { scale, fade } from 'svelte/transition';

	let modalOpen = false;

	let modal: HTMLDivElement;

	async function handleOpenModal() {
		modalOpen = true;
	}

	async function closeModal() {
		modalOpen = false;
	}
</script>

<button class="open-modal-btn positioned-modal-button" on:click={handleOpenModal}>
	Abrir Modal 2
</button>

<button class="open-modal-btn" on:click={handleOpenModal}> Abrir Modal </button>
{#if modalOpen}
	<div
		class="bg"
		on:click={closeModal}
		on:keydown
		in:fade={{ duration: 300 }}
		out:fade={{ duration: 300 }}
	>
		<div
			on:click|stopPropagation
			on:keydown
			bind:this={modal}
			in:scale={{ start: 0.8, duration: 300 }}
			out:scale={{ start: 0.6, duration: 300 }}
			class="content"
			id="modal"
		>
			<h2>Modal para eu roubar o seu nome</h2>
			<div class="label-wrapper">
				<label for="first-name">Nome</label>
				<input
					type="text"
					name="first-name"
					id="first-name"
					placeholder="Seu nome aqui"
					aria-label="Input para nome"
				/>
			</div>
			<div class="label-wrapper">
				<label for="last-name">Sobrenome</label>
				<input
					type="text"
					id="last-name"
					name="last-name"
					aria-label="Input para sobrenome"
					placeholder="Seu sobrenome aqui"
				/>
			</div>
			<div>
				<button on:click={closeModal}>Fechar Modal</button>
			</div>
		</div>
	</div>
{/if}

<style>
	.bg {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.content {
		display: flex;
		flex-direction: column;
		justify-content: start;
		align-items: start;
		gap: 1rem;

		min-height: 500px;
		min-width: 500px;
		border: 1px solid #fdfdfd;
		background-color: #0d0d0d;
		padding: 1rem;
		border-radius: 0.5rem;
	}

	.label-wrapper {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}

	input {
		background-color: transparent;
		border: 1px solid #fdfdfd;
		border-radius: 4px;
		padding: 0.5rem 1rem;
		width: 100%;

		font-size: 1rem;
	}

	button {
		background-color: transparent;
		border: 2px solid #fdfdfd;
		padding: 0.5rem 1rem;
		width: 100%;
		transition: color 0.2s ease-in-out, background-color 0.2s ease-in-out;
		border-radius: 4px;
		cursor: pointer;
	}

	button:hover,
	button:focus {
		background-color: #fdfdfd;
		color: #000000;
	}

	.open-modal-btn {
		max-width: 120px;
	}

	.hidden {
		display: none;
	}

	.positioned-modal-button {
		position: absolute;
		top: 100px;
		left: 100px;
	}
</style>
