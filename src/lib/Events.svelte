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
	]
</script>

<div class="header__events">	
	{#each events as event}
		<div class="header__event">
			<p class="header__event-category">{event.category}</p>
			<p class="header__event-date">{event.date}</p>
			<p class="header__event-title">{event.title}</p>
		</div>
	{/each}
</div>

<style>
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