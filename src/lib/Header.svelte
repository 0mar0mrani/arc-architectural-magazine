<script>
	import { onMount } from 'svelte';
	import Logo from './assets/svg/Logo.svelte';
	import Menu from './assets/svg/Menu.svelte';
	import Close from './assets/svg/Close.svelte';

	let isMenuOpen = false;
	let isSticky = false;
	let logoElement;
	let headerMenuWElement;
	let headerElement;

	const color1 = '#000';
	const color2 = '#9747ff';
	let color = '#000';

	onMount(() => {
		handleWindowScroll();
	});

	function handleMenuButtonClick() {
		isMenuOpen = !isMenuOpen;
	}

	function changeColor() {
		if (color === color1) {
			color = color2;
		} else {
			color = color1;
		}
	}

	function handleWindowScroll() {
		const rect = logoElement.getBoundingClientRect();
		const scroll = window.scrollY; 
		const logoHeightPlusMargin = rect.top + scroll + 10;
		const headerMenuHeight = headerMenuWElement.offsetHeight;
		
		if (scroll > logoHeightPlusMargin) {
			isSticky = true;
			headerElement.style.marginBottom = `${headerMenuHeight}px`
		} else {
			isSticky = false;
			headerElement.style.marginBottom = '0px'
		}
	}
</script>

<svelte:window on:scroll={handleWindowScroll}/>

<header class="header" bind:this={headerElement}>
	<a href="/" on:mouseenter={changeColor} on:mouseleave={changeColor} bind:this={logoElement} class="header__logo">
		<Logo {color} />
	</a>

	<div class={`header__menu ${isSticky ? 'header__menu--fixed' : ''}`} bind:this={headerMenuWElement}>
		<h1 class="header__name">Arc Architectural</h1>

		<button class="header__menu-button" on:click={handleMenuButtonClick}>
			{#if isMenuOpen}
					<Close/>
				{:else}
					<Menu/>
			{/if}
		</button>

		{#if isMenuOpen}
			<nav class="header__navigation">
				<ul>
					<li>
						<a href="#">
							Announcements
						</a>
					</li>

					<li>
						<a href="#">
							Journal
						</a>
					</li>

					<li>
						<a href="">
							Reviews
						</a>
					</li>

					<li>
						<a href="">
							Books
						</a>
					</li>

					<li>
						<a href="">
							Information
						</a>
					</li>
				</ul>
			</nav>	
		{/if}
	</div>
</header>

<style>
	.header {
		grid-column: 1 / 13;
	}

	.header__menu {
		display: flex;
		justify-content: space-between;
		align-items: center;
		position: relative;
		padding: 2rem 0;
		background-color: #fff;
		transform: scale(1.001);
	}
	
	.header__menu--fixed {
		position: fixed;
		top: 0;
		width: calc(100% - 2rem);
	}

	.header__name {
		font: var(--font-large-text);
	}

	.header__menu-button {
		flex-shrink: 0;
	}

	.header__navigation {
		position: absolute;
		top: 100%;
		left: 0;
		width: 100%;
		border-top: solid 1px #000;
		border-bottom: solid 1px #000;
		background-color: #fff;
		padding: 2rem 0;
		font-size: 4rem;
	}
</style>
