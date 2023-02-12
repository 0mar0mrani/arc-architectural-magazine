<script lang="ts">
	import ArticleCard from '$lib/ArticleCard.svelte';
	import type { ArticleType } from '../types';

	export let articles: ArticleType[];
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