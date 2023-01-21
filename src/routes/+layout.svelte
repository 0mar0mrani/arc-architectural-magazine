<script>
	import '../global/css/main.svelte'
	import Header from '../lib/Header.svelte';
</script>

<div class="layout">
	<Header/>

	<slot></slot>
</div>

<style>
	.layout {
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		margin: 1rem;
	}
</style>