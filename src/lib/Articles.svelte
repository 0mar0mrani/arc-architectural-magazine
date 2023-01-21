<script>
	import ArticleCard from '$lib/ArticleCard.svelte';

	const articles = [
		{
			header: 'Anhalt University of Applied Sciences',
			title: 'Dessau Summer School of Architecture',
			image: '$lib/assets/images/alan-rostovtev.jpg',
			alt: 'White wall',
			link: '/article',
		},
		{
			header: 'ArkDes',
			title: 'Joar Nango: Girjegumpi',
			image: '$lib/assets/images/mohammad-mohsen-rohani.jpg',
			alt: 'White building',
			link: '/article',
		},
		{
			header: 'Sabu Kohso',
			title: 'Nuclear Recursivity and Seismic Awakening',
			image: '$lib/assets/images/albert-stoynov.jpg',
			alt: 'Angled building',
			link: '/article',
		},
		{
			header: 'Bauhaus Dessau Foundation',
			title: 'Bauhaus Lab 2023: Concrete Antarctic',
			image: '$lib/assets/images/brice-cooper.jpg',
			alt: 'Building with bridge',
			link: '/article',
		},
		{
			header: 'Radiowaves Collective',
			title: 'Mothering a Movement: Notes from India’s Longest Anti-Nuclear Struggle',
			image: '$lib/assets/images/alan-rostovtev-article.jpg',
			alt: 'Glass building',
			link: '/article',
		},
		{
			header: 'Livia Krohn Miller',
			title: 'Ten Thousand Years of Isolation',
			image: '$lib/assets/images/refargotohp.jpg',
			alt: 'White building',
			link: '/article',
		},
		{
			header: 'AA editorial',
			title: 'The Avant-Garde Museum',
			image: '$lib/assets/images/tingfeng-xia.jpg',
			alt: 'Bridge',
			link: '/article',
		},
	]
</script>

{#each articles as article}
	<ArticleCard
		header={article.header}
		title={article.title}
		src={article.image}
		alt={article.alt}
		href={article.link}
	/>
{/each}