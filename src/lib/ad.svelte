<section class="ads">
	<div class="ads__ad">
		<p>(ad placeholder)</p>

		<p>4:3</p>
	</div>

	<div class="ads__ad">
		<p>(ad placeholder)</p>

		<p>4:3</p>
	</div>

	<div class="ads__ad">
		<p>(ad placeholder)</p>

		<p>4:3</p>
	</div>

	<div class="ads__ad">
		<p>(ad placeholder)</p>

		<p>4:3</p>
	</div>
</section>

<style>
	.ads {
		grid-column: 1 / 10;
		display: flex;
		gap: 1rem;
		padding: 1rem;
		flex-direction: column;
		font: var(--font-large-text);
		color: var(--primary-color);
		background: url('https://i.postimg.cc/mkmDF6v3/ad-background.jpg');
		background-size: contain;
	}
	
	.ads__ad {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: var(--tertiary-color);
		aspect-ratio: 4 / 3;
	}

	@media only screen and (min-width: 800px) {
		.ads {
			display: grid;
			grid-template-columns: repeat(2, 1fr);
			gap: 1rem;
			padding: 1rem;
		}
		
		.ads__ad,
		.ads__ad:first-child {
			margin: 0;
		}
	}
</style>