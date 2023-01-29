<script>
	import ArticleCard from '$lib/ArticleCard.svelte';

	export let articles;
</script>

{#each articles as article}
	<ArticleCard
		header={article.header}
		title={article.title}
		src={article.image}
		alt={article.alt}
		href={article.link}
		gridClass={article.gridClass}
	/>
{/each}