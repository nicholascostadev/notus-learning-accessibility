<script lang="ts">
	import { onMount, tick } from 'svelte';
	import { scale, fade } from 'svelte/transition';

	let modalOpen = false;
	let closeButton: HTMLButtonElement;

	const focusableElements = 'button, input, [tabindex]:not([tabindex="-1"])';
	let modal: HTMLDivElement;

	let modalFirstInput: HTMLInputElement;
	let lastFocusableElement: HTMLButtonElement;
	let focusableContent: NodeListOf<HTMLElement>;

	onMount(() => {
		focusableContent = modal?.querySelectorAll(focusableElements);
	});

	async function handleOpenModal() {
		modalOpen = true;
		await tick();
		modalFirstInput.focus();
	}

	async function closeModal() {
		modalOpen = false;
		await tick();
		closeButton.focus();
	}

	function handleKeydown(event: KeyboardEvent) {
		if (!modalOpen) return;
		if (event.key === 'Escape') {
			closeModal();
		}

		let isTabPressed = event.key === 'Tab';

		if (!isTabPressed) {
			return;
		}

		if (event.shiftKey) {
			if (document.activeElement === modalFirstInput) {
				lastFocusableElement.focus();
				event.preventDefault();
			}
		} else {
			if (document.activeElement === lastFocusableElement) {
				modalFirstInput.focus();
				event.preventDefault();
			}
		}
	}
</script>

<svelte:window on:keydown={handleKeydown} />

<button class="open-modal-btn-2" on:click={handleOpenModal}>Abrir Modal 2</button>

<button bind:this={closeButton} class="open-modal-btn" on:click={handleOpenModal}>
	Abrir Modal
</button>
{#if modalOpen}
	<div
		class="bg"
		on:click={closeModal}
		on:keydown
		tabIndex="-1"
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
			tabIndex="-1"
			role="dialog"
			aria-labelledby="modal-title"
			aria-modal="true"
		>
			<h2 id="modal-title">Modal para fazer tal coisa</h2>
			<input
				bind:this={modalFirstInput}
				type="text"
				name="text"
				placeholder="Escreva o que quiser"
				aria-label="Input pra texto legal"
			/>
			<input
				type="text"
				name="teste"
				aria-label="Input pra outro texto"
				placeholder="Escreve aí pô"
			/>
			<div>
				<button on:click={closeModal} bind:this={lastFocusableElement}>Fechar Modal</button>
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

	input {
		background-color: transparent;
		border: 1px solid #fdfdfd;
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

	.open-modal-btn-2 {
		display: none;
		position: absolute;
		top: 100px;
		left: 100px;
		max-width: 120px;
	}
</style>
