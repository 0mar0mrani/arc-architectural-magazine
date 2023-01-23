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
		margin: 1rem;
		position: relative;
		column-gap: 1rem;
	}

	@media only screen and (min-width: 1000px) {
		.layout {
			margin-top: 0;
			margin-bottom: 0;
		}
	}
</style>