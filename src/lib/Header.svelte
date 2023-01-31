<script>
	import { onMount } from 'svelte';

	import Events from '$lib/Events.svelte'

	import Logo from './assets/svg/Logo.svelte';
	import Menu from './assets/svg/Menu.svelte';
	import Close from './assets/svg/Close.svelte';
	import Search from './assets/svg/Search.svelte';

	const articles = [
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

	let isMenuOpen = false;
	let isSticky = false;
	let isSearchOpen = false;
	let searchString = '';

	let filteredArticles = filterArticles();
	
	let logoElement;
	let headerMenuWElement;
	let headerElement;
	let inputEl;

	onMount(() => {
		setIsSticky();
		setDesktopHeader();
	});

	function handleMenuButtonClick() {
		isSearchOpen = false;
		searchString = '';
		isMenuOpen = !isMenuOpen;
	}

	function handleSearchButtonClick() {
		isMenuOpen = false;
		isSearchOpen = !isSearchOpen;

		if (searchString !== '') {
			searchString = '';
		} else {
			setTimeout(() => {
				inputEl.focus();
			}, 0.3 * 1000) 
		}
	}

	function handleSearchInput(event) {
		const stringInput = event.currentTarget.value;
		setFilterString(stringInput);
		filteredArticles = filterArticles();
	}

	function handleResultClick() {
		isSearchOpen = false;
		isMenuOpen = false;
		searchString = '';
	}

	function handleLogoClick() {
		isMenuOpen = false;
		isMenuOpen = false;
		searchString = '';
	}

	function filterArticles() {
		if (searchString !== '') {
			const filterToCompare = searchString.toLowerCase();

			return articles.filter(article => {
				const titleToCompare = article.title.toLowerCase();

				return titleToCompare.includes(filterToCompare);
			});
		} else {
			return articles;
		}
	}
	
	function setFilterString(string) {
		searchString = string;
	}

	function handleWindowScroll() {
		setIsSticky();
	}

	function handleWindowResize() {
		setDesktopHeader();
	}

	function setDesktopHeader() {
		const screenWidth = window.innerWidth;
		const desktop = 800;

		if (screenWidth >= desktop) {
			isMenuOpen = true;
		} else {
			isMenuOpen = false;
		}
	}

	function setIsSticky() {
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

<svelte:window on:scroll={handleWindowScroll} on:resize={handleWindowResize}/>

<header class="header" bind:this={headerElement}>
	<a href="/" bind:this={logoElement} on:click={handleLogoClick}>
		<Logo/>
	</a>

	<div class={`header__menu ${isSticky ? 'header__menu--fixed' : ''}`} bind:this={headerMenuWElement}>
		<div class="header__menu-name-button-container">
			<h1 class="header__name">Arc Architectural</h1>

			<div class="header__button-container">

				{#if !isMenuOpen}
					<input 
						type="text" 
						class="header__search-input" 
						class:header__search-input--open={isSearchOpen} 
						placeholder="search"
						bind:this={inputEl}
						bind:value={searchString}
						on:input={handleSearchInput}
					>	
				{/if}
				
				<button class="header__menu-button header__menu-button--search" on:click={handleSearchButtonClick}>
					<Search
						{isSearchOpen}
					/>
				</button>
				
				<button class="header__menu-button" on:click={handleMenuButtonClick}>
					{#if isMenuOpen}
						<Close/>
					{:else}
						<Menu/>
					{/if}
				</button>
			</div>

			{#if searchString !== ''}
				<ul class="header__search-results">
					{#each filteredArticles as article}
						<li class="header__search-item">
							<a href={article.link} on:click={handleResultClick}>
								<div class="header__search-item-image">
									<img src={article.image} alt={article.alt}>
								</div>
								
								<div  class="header__search-item-title">
									<p>{article.title}</p>
								</div>
							</a>
						</li>
					{/each}
				</ul>
			{/if}
		</div>

		<div class="header__main-container">
			{#if isMenuOpen}
				<div class="header__about">
					<p>
						AA was founded in 1847 with the aspiration of ‘promoting and affording facilities for the study of architecture for the public benefit’. Likeness it them very firmament without created also bring a one Whose she'd in. Sea unto created every together together. For that wherein. Kind sea earth them was place. Sixth signs saying after replenish multiply. Female every unto beginning appear moving tree the bearing own.
					</p>
				</div>

				<nav class="header__navigation">
					<ul>
						<li>
							<a href="/information">
								Announcements
							</a>
						</li>

						<li>
							<a href="/information">
								Journal
							</a>
						</li>

						<li>
							<a href="/information">
								Reviews
							</a>
						</li>

						<li>
							<a href="/information">
								Books
							</a>
						</li>

						<li>
							<a href="/information">
								Information
							</a>
						</li>
					</ul>
				</nav>

				<Events/>
			{/if}
		</div>
	</div>
</header>

<style>
	.header {
		grid-column: 1 / 13;
		z-index: 10;
	}

	.header__menu {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		position: relative;
		transform: scale(1.001);
	}

	.header__menu-name-button-container {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 2rem 0;
		background-color: var(--primary-color);
	}

	.header__main-container {
		overflow-y: scroll;
		max-height: calc(100dvh - 9rem);
		background-color: var(--primary-color);
	}
	
	.header__menu--fixed {
		position: fixed;
		top: 0;
		width: calc(100% - 2rem);
	}

	.header__name {
		font: var(--font-large-text);
	}

	.header__button-container {
		display: flex;
		align-items: center;
		gap: 1.5rem;
	}

	.header__menu-button {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 4.4rem;
		height: 4.4rem;
	}

	.header__menu-button--search {
		width: 3rem;
		height: 3rem;
		position: relative;
	}

	.header__search-input {
		position: absolute;
		right: 0;
		top: 50%;
		transform: translateY(-50%);
		font: var(--font-large-text);
		background-color: var(--primary-color);
		color: var(--secondary-color);
		border: none;
		border-bottom: solid 0.4rem var(--secondary-color);
		transition: width 0.2s ease-in;
		margin-right: 10.5rem;
		width: 0;
		padding-left: 0;
	}
	
	.header__search-input--open {
		width: calc(100% - 10.5rem);
		padding-left: 0.5rem;
	}

	.header__search-input::placeholder {
		color: var(--secondary-color);
		opacity: 0.3;
		transition: all 0.2s;
		transform: translateY(100%);
		transition-delay: 0.2s;
	}

	.header__search-input--open::placeholder {
		transform: translateY(0);
	}

	.header__search-results {
		position: absolute;
		top: 100%;
		left: 0;
		width: 100%;
		max-height: calc(100dvh - 8.8rem);
		overflow-y: scroll;
		background-color: var(--primary-color);
		transform: scale(1.005);
		display: flex;
		flex-direction: column;
	}

	.header__search-item a {
		display: flex;
		padding: 2rem;
	}

	.header__search-item:not(:last-child) {
		border-bottom: solid 0.1rem var(--secondary-color);
	}

	.header__search-item-image {
		width: 10rem;
		height: 10rem;
		aspect-ratio: 1 / 1;
		background-color: red;
	}

	.header__search-item-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.header__search-item-title {
		display: flex;
		align-items: flex-end;
		padding-left: 1rem;
	}
	
	.header__about {
		font: var(--font-body-text);
		padding: 2rem 0;
		border-top: solid 1px var(--secondary-color);
		border-bottom: solid 1px var(--secondary-color);
	}

	.header__navigation {
		width: 100%;
		border-bottom: solid 1px var(--secondary-color);
		background-color: var(--primary-color);
		padding: 2rem 0;
		font-size: 4rem;
	}

	@media screen and (min-width: 800px) {
		.header {
			grid-column: 1 / 4;
			height: 100dvh;
			overflow-y: scroll;
			padding-top: 1rem;
		}

		.header__menu-button {
			display: none;
		}

		.header__menu--fixed {
			position: relative;
			width: unset;
		}

		.header__main-container {
			overflow-y: unset;
			max-height: unset;
		}
	}
</style>
