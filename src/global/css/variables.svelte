<style>
	:global(:root) {
		--primary-color: var(--primary-color);
		--secondary-color: #000000;
		--tertiary-color: #9747ff;
		--quaternary-color: #e7e7e7;

		--font-body-text: 2rem 'Times New Roman';
		--font-body-text-uppercase: 2rem Uppercase 'Times New Roman';
		--font-large-text: 4rem/4.8rem 'neue-haas-grotesk-text', sans-serif;
		--font-small-text: 1rem;
		--font-small-text-uppercase: 1rem/1.2rem Uppercase 'Times New Roman';
	}

	:global(body:has(.dark-mode)) {
		--primary-color: #000;
		--secondary-color: #fff;
	}
</style>