<script>
	export let isSearchOpen;
</script>

<svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg" class:open={isSearchOpen}>
	<circle cx="11.5" cy="11.5" r="9.5" stroke="black" stroke-width="4"/>
	<path d="M19 19L30 30" stroke="black" stroke-width="4"/>
</svg>
	

<style>
	circle,
	path {
		stroke: var(--secondary-color);
	}

	.open circle,
	.open path {
		stroke: var(--tertiary-color);
	}
</style>
	