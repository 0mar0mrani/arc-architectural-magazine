<script>
	import Articles from '$lib/Articles.svelte'
</script>

<div class="articles-container">
	<Articles/>
</div>

<style>
	.articles-container {
		grid-column: 1 / 13;
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	@media only screen and (min-width: 1000px) {
		.articles-container {
			padding-top: 1rem;
			grid-column: 4 / 13;
			display: grid;
			grid-template-columns: repeat(9, 1fr);
			height: 100dvh;
			overflow-y: scroll;
		}
	}
</style>