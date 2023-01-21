<script>
	import ArticleCard from '$lib/ArticleCard.svelte';

	const articles = [
		{
			header: 'Anhalt University of Applied Sciences',
			title: 'Dessau Summer School of Architecture',
			image: 'https://i.postimg.cc/B6v5j0qF/alan-rostovtev.jpg',
			alt: 'White wall',
			link: '/article',
		},
		{
			header: 'ArkDes',
			title: 'Joar Nango: Girjegumpi',
			image: 'https://i.postimg.cc/9XKPQKs4/mohammad-mohsen-rohani.jpg',
			alt: 'White building',
			link: '/article',
		},
		{
			header: 'Sabu Kohso',
			title: 'Nuclear Recursivity and Seismic Awakening',
			image: 'https://i.postimg.cc/FHQjjcrN/albert-stoynov.jpg',
			alt: 'Angled building',
			link: '/article',
		},
		{
			header: 'Bauhaus Dessau Foundation',
			title: 'Bauhaus Lab 2023: Concrete Antarctic',
			image: 'https://i.postimg.cc/HxPw5hxh/brice-cooper.jpg',
			alt: 'Building with bridge',
			link: '/article',
		},
		{
			header: 'Radiowaves Collective',
			title: 'Mothering a Movement: Notes from India’s Longest Anti-Nuclear Struggle',
			image: 'https://i.postimg.cc/jjcQq5rK/alan-rostovtev-article.jpg',
			alt: 'Glass building',
			link: '/article',
		},
		{
			header: 'Livia Krohn Miller',
			title: 'Ten Thousand Years of Isolation',
			image: 'https://i.postimg.cc/Hk4b3xn5/refargotohp.jpg',
			alt: 'White building',
			link: '/article',
		},
		{
			header: 'AA editorial',
			title: 'The Avant-Garde Museum',
			image: 'https://i.postimg.cc/Hk4b3xn5/refargotohp.jpg',
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