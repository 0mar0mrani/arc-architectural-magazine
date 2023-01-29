<script>
	import { onMount } from 'svelte';

	import Close from '$lib/assets/svg/Close.svelte';

	let isOpen = true;
	let subscribeTextEl;

	onMount(() => {
		setText();
	})

	function handleButtonClick() {
		isOpen = false
	}

	function handleWindowResize() {
		setText();
	}

	function setText() {
		const desktopLayout = 800;

		if (window.innerWidth > desktopLayout) {
			subscribeTextEl.innerText = 'Subscribe for architecture, art, and more';
		} else {
			subscribeTextEl.innerText = 'Subscribe';
		}
	}
</script>

<svelte:window on:resize={handleWindowResize}/>

{#if isOpen}
	<button class="subscribe">
		<p bind:this={subscribeTextEl}>Subscribe</p>

		<button class="subscribe__close-button" on:click|stopPropagation={handleButtonClick}>
			<Close/>
		</button>
	</button>
{/if}

<style>
	.subscribe {
		display: flex;
		justify-content: space-between;
		align-items: center;
		background-color: var(--quaternary-color);
		position: sticky;
		bottom: 1rem;
		left: 0;
		right: 0;
		border-radius: 1rem;
		font: var(--font-large-text);
		padding: 0.7rem 1.5rem;
		grid-column: 1 / 10;
	}

	.subscribe__close-button {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 5rem;
		height: 5rem;
		z-index: 10;
	}

	@media only screen and (min-width: 800px) {

	}
</style>