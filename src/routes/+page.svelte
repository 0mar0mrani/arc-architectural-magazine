<script>
	import Articles1 from '$lib/Articles.svelte'
	import Ad from '$lib/ad.svelte'
	import Subscribe from '$lib/Subscribe.svelte';

	document.documentElement.dataset.theme = '';

	const articles1 = [
		{
			header: 'Anhalt University of Applied Sciences',
			title: 'Dessau Summer School of Architecture',
			image: 'https://i.postimg.cc/B6v5j0qF/alan-rostovtev.jpg',
			alt: 'White wall',
			link: '/article',
			gridClass: 'article-overview__full-width order1',
		},
		{
			header: 'ArkDes',
			title: 'Joar Nango: Girjegumpi',
			image: 'https://i.postimg.cc/9XKPQKs4/mohammad-mohsen-rohani.jpg',
			alt: 'White building',
			link: '/article',
			gridClass: 'article-overview__span4 order2',
		},
		{
			header: 'Sabu Kohso',
			title: 'Nuclear Recursivity and Seismic Awakening',
			image: 'https://i.postimg.cc/FHQjjcrN/albert-stoynov.jpg',
			alt: 'Angled building',
			link: '/article',
			gridClass: 'article-overview__span5x2 order1',
		},
		{
			header: 'Bauhaus Dessau Foundation',
			title: 'Bauhaus Lab 2023: Concrete Antarctic',
			image: 'https://i.postimg.cc/HxPw5hxh/brice-cooper.jpg',
			alt: 'Building with bridge',
			link: '/article',
			gridClass: 'article-overview__span4',
		},
	]

	const articles2 = [
		{
			header: 'Radiowaves Collective',
			title: 'Mothering a Movement: Notes from India’s Longest Anti-Nuclear Struggle',
			image: 'https://i.postimg.cc/gkhVX4Pg/op23.jpg',
			alt: 'Glass building',
			link: '/article',
			gridClass: 'article-overview__full-width',
		},
		{
			header: 'Livia Krohn Miller',
			title: 'Ten Thousand Years of Isolation',
			image: 'https://i.postimg.cc/Hk4b3xn5/refargotohp.jpg',
			alt: 'White building',
			link: '/article',
			gridClass: 'article-overview__span5',
		},
		{
			header: 'AA editorial',
			title: 'The Avant-Garde Museum',
			image: 'https://i.postimg.cc/GtWvgTvP/tingfeng-xia.jpg',
			alt: 'Bridge',
			link: '/article',
			gridClass: 'article-overview__span4',
		},
	]
</script>

<div class="container">
	<Articles1
		articles={articles1}
	/>

	<Ad/>

	<Articles1
		articles={articles2}
	/>

	<Subscribe/>
</div>

<style>
	.container {
		grid-column: 1 / 13;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		position: relative;
	}

	@media only screen and (min-width: 800px) {
		.container {
			padding: 1rem 0;
			grid-column: 4 / 13;
			display: grid;
			grid-template-columns: repeat(9, 1fr);
			height: 100vh;
			height: 100dvh;
			overflow-y: scroll;
		}
	}
</style>