<script>
	import Logo from './assets/svg/Logo.svelte';
	import Menu from './assets/svg/Menu.svelte';
	import Close from './assets/svg/Close.svelte';

	let isMenuOpen = false;

	const color1 = '#000';
	const color2 = '#9747ff';
	let color = '#000';

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
</script>

<header class="header">
	<a href="/" on:mouseenter={changeColor} on:mouseleave={changeColor}>
		<Logo {color} />
	</a>

	<div class="header__menu">
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
		margin-top: 2rem;
		margin-bottom: 4rem;
	}

	.header__name {
		font: var(--font-large-text);
	}

	.header__menu-button {
		flex-shrink: 0;
	}

	.header__navigation {
		position: absolute;
		top: 130%;
		left: 0;
		width: 100%;
		border-top: solid 1px #000;
		border-bottom: solid 1px #000;
		background-color: #fff;
		padding: 2rem 0;
		font-size: 4rem;
	}
</style>