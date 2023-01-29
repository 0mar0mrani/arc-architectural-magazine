<script>
	import '../global/css/main.svelte'
	import Header from '/src/lib/Header.svelte';
</script>

<div class="layout">
	<Header/>

	<slot></slot>
</div>

<style>
	.layout {
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		padding: 1rem;
		position: relative;
		column-gap: 1rem;
		max-width: 170rem;
		margin: 0 auto;
	}

	@media only screen and (min-width: 800px) {
		.layout {
			padding-top: 0;
			padding-bottom: 0;
		}
	}
</style>