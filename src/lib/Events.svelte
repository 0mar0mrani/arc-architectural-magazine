<script>
	export let category = '';
	export let date = '';
	export let title = '';

	const events = [	
		{
			category: 'Lectures',
			date: 'January 20 12:00-14:00',
			title: 'Conversation: Sami Sami sacred mountains and sacrificial stones'
		},
		{
			category: 'Exhibitions',
			date: 'February 5 16:00–17:00',
			title: 'Free guided tour in Kunna Guanna Concha'
		},
		{
			category: 'Exhibitions',
			date: 'February 12 18:00',
			title: 'Exhibition opening: Metahaven and Susanne M. Winterling'
		},
		{
			category: 'Open Seminars',
			date: 'March 4 18:00–20:00',
			title: 'Monumental love – Art historian Marit Paasche on Hannah Ryggen'
		},
		{
			category: 'Lectures',
			date: 'January 20 12:00-14:00',
			title: 'Conversation: Sami Sami sacred mountains and sacrificial stones'
		},
		{
			category: 'Exhibitions',
			date: 'February 5 16:00–17:00',
			title: 'Free guided tour in Kunna Guanna Concha'
		},
		{
			category: 'Exhibitions',
			date: 'February 12 18:00',
			title: 'Exhibition opening: Metahaven and Susanne M. Winterling'
		},
		{
			category: 'Open Seminars',
			date: 'March 4 18:00–20:00',
			title: 'Monumental love – Art historian Marit Paasche on Hannah Ryggen'
		},
		{
			category: 'Lectures',
			date: 'January 20 12:00-14:00',
			title: 'Conversation: Sami Sami sacred mountains and sacrificial stones'
		},
		{
			category: 'Exhibitions',
			date: 'February 5 16:00–17:00',
			title: 'Free guided tour in Kunna Guanna Concha'
		},
		{
			category: 'Exhibitions',
			date: 'February 12 18:00',
			title: 'Exhibition opening: Metahaven and Susanne M. Winterling'
		},
		{
			category: 'Open Seminars',
			date: 'March 4 18:00–20:00',
			title: 'Monumental love – Art historian Marit Paasche on Hannah Ryggen'
		},
		{
			category: 'Lectures',
			date: 'January 20 12:00-14:00',
			title: 'Conversation: Sami Sami sacred mountains and sacrificial stones'
		},
		{
			category: 'Exhibitions',
			date: 'February 5 16:00–17:00',
			title: 'Free guided tour in Kunna Guanna Concha'
		},
		{
			category: 'Exhibitions',
			date: 'February 12 18:00',
			title: 'Exhibition opening: Metahaven and Susanne M. Winterling'
		},
		{
			category: 'Open Seminars',
			date: 'March 4 18:00–20:00',
			title: 'Monumental love – Art historian Marit Paasche on Hannah Ryggen'
		},
	]

	let currentFilter = null;
	let filteredEvents = filterEvents();

	function handleEventButtonClick(event) {
		setCurrentFilter(event);
		filteredEvents = filterEvents();
	}

	function setCurrentFilter(event) {
		const buttonName = event.currentTarget.innerHTML;

		if (buttonName === currentFilter) {
			currentFilter = null;
		} else {
			currentFilter = buttonName;
		}
	}

	function filterEvents() {
		const eventsCopy = [...events];

		if (currentFilter === null) {
			return events;
		} else {
			return eventsCopy.filter(event => event.category.toLowerCase() === currentFilter)
		}
	}
</script>

<div class="header__events-container">	
	<div>
		<p>UPCOMING EVENTS</p>
	
		<div class="header__event-buttons">
			<button class="header__event-button" on:click={handleEventButtonClick}>lectures</button>
	
			<button class="header__event-button" on:click={handleEventButtonClick}>exhibitions</button>
	
			<button class="header__event-button" on:click={handleEventButtonClick}>open seminars</button>
		</div>
	</div>

	<div class="header__events">
		{#each filteredEvents as event}
			<div class="header__event">
				<p class="header__event-category">{event.category}</p>
				<p class="header__event-date">{event.date}</p>
				<p class="header__event-title">{event.title}</p>
			</div>
		{/each}
	</div>
</div>

<style>
	.header__event-button {
		color: inherit;
		text-transform: uppercase;
	}

	.header__events {
		display: flex;
		flex-direction: column;
		gap: 2rem;
		margin: 2rem 0;
	}

	.header__event-category,
	.header__event-date {
		font: var(--font-small-text);
		text-transform: uppercase;
	}
</style>