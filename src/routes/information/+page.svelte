<script>
	import { onMount } from 'svelte';
	
	let src;
	const mobileImage = 'https://i.postimg.cc/5tbSMzTn/alan-rostovtev-information.jpg';
	const desktopImage = 'https://i.postimg.cc/d3k89jZt/or-hakim.jpg';

	function handleWindowResize() {
		setImage();
	}

	function setImage() {
		if (window.innerWidth < 800) {
			src = mobileImage;
		} else {
			src = desktopImage;
		}
	}

	onMount(() => {
		setImage();
	})
</script>

<svelte:window on:resize={handleWindowResize}/>

<div class="information__container">
	<h2 class="information__header">Information</h2>

	<div class="information__image">
		<!-- svelte-ignore a11y-img-redundant-alt -->
		<img {src} alt="Photo-light">
	</div>

	<h3 class="information__sub-header">
		AA was founded in 1847 with the aspiration of ‘promoting and affording facilities for the study of architecture for the public benefit’
	</h3>

	<div class="information__paragraphs">
		<p>
			Said every spirit earth grass, which. Whales lesser winged bring second light replenish was heaven tree subdue, set Let all kind own you're hath lights to meat years. Form bearing have You're which meat she'd grass life one saw earth bring likeness beast from Great he.
			Make multiply won't together they're creature you'll moving over dominion to them male earth so signs, life and meat shall subdue likeness life Give open dominion second days upon moved.
		</p>

		<p>
			Light, whose our firmament give you place open can't lesser beast brought you're night days have in rule may created in brought there life divided place fourth creepeth. Abundantly night fly.
		</p>

		<p>
			Upon, him deep divide fill, god unto. Meat air. Greater. Saw herb rule heaven them shall face, moved living called face brought itself living blessed brought his creeping is darkness living second gathered it.
			Air you'll moving above creeping firmament, for for said female fish creepeth them sea fruit living which their grass for brought was, appear sea had day appear god fruitful.
		</p>

		<p>
			Their wherein us moveth fish, which our life deep abundantly cattle wherein. For him. Whales give greater won't void rule dry. To spirit upon deep them midst. Creature first. Fourth.
		</p>
	</div>
</div>


<style>
	.information__container {
		grid-column: 1 / 13;
		margin: 2rem 0;
		display: flex;
		flex-direction: column;
	}

	.information__header,
	.information__sub-header {
		font: var(--font-large-text);
	}

	.information__image {
		margin: 4rem 0;
	}

	.information__paragraphs {
		margin-top: 4rem;
	}

	.information__paragraphs p:not(:first-child){
		text-indent: 5.5rem;
	}

	@media only screen and (min-width: 800px) {
		.information__container {
			display: grid;
			grid-template-columns: repeat(9, 1fr);
			gap: 1rem;
			grid-column: 4 / 13;
			margin-top: 0;
			padding: 2rem 0;
			height: 100dvh;
			overflow-y: scroll;
			margin: 0;
		}
		
		.information__header,
		.information__image {
			grid-column: 2 / 9;
		}
		
		.information__sub-header {
			grid-column: 2 / 8;
		}

		.information__paragraphs {
			grid-column: 2 / span 4;
		}
	}
</style>