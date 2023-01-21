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
</style>