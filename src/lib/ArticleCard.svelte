<script>
	export let header = '';
	export let title = '';
	export let src = '';
	export let alt = '';
	export let href = '';
</script>

<a class="article-overview" {href}>
	<div class="article-overview__image">
		<img {src} {alt}>
	</div>

	<div class="article-overview__card">
		<p class="article-overview__header">{header}</p>
		<p class="article-overview__title">{title}</p>
	</div>
</a>

<style>
	.article-overview {
		display: flex;
		flex-direction: column;
	}

	.article-overview__image {
		width: 100%;
	}

	.article-overview__image img {
		width: 100%;
		height: auto;
		display: block;
	}

	.article-overview__card {
		color: var(--secondary-color);
		background-color: var(--primary-color);
		padding: 1.6rem 1.6rem 5rem 1.6rem;
	}

	.article-overview__header {  
		font: var(--font-body-text);
	}

	.article-overview__title {
		font: var(--font-large-text);
	}
</style>