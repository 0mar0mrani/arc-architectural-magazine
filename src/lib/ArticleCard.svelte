<script>
	export let header = '';
	export let title = '';
	export let src = '';
	export let alt = '';
	export let href = '';
	export let gridClass = '';
</script>

<a class="article-overview {gridClass}" {href}>
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
		color: var(--primary-color);
		background-color: var(--secondary-color);
		padding: 1.6rem 1.6rem 5rem 1.6rem;
	}

	.article-overview__header {  
		font: var(--font-body-text);
	}

	.article-overview__title {
		font: var(--font-large-text);
	}

	@media only screen and (min-width: 1000px) {
		.article-overview__full-width {
			grid-column: span 9;
		}

		.article-overview__span5x2 {
			grid-column: span 5;
			grid-row: span 2;
		}
		
		.article-overview__span4 {
			grid-column: span 4;
		}

		.article-overview__span5 {
			grid-column: span 5;
		}

		.article-overview__card {
			display: none;
		}

		.order1 {
			order: -2;
		}

		.order2 {
			order: -1;
		}

		.order3 {
			order: 0;
		}
	}
</style>