<script>
	import Logo from './assets/svg/logo.svelte';
	const color1 = '#000';
	const color2 = '#9747ff';
	let color = '#000';

	function changeColor() {
		if (color === color1) {
			color = color2;
		} else {
			color = color1;
		}
	}

</script>

<header class="header">
	<a 
	href="/"
	on:mouseenter={changeColor} 
	on:mouseleave={changeColor}>
		<Logo
		 	{color}
		/>
	</a>

</header>

<style>
	.header {
		grid-column: 1 / 13;
	}
</style>