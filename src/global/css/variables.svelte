<style>
	:global(:root) {
		--primary-color: #fff;
		--secondary-color: #000000;
		--tertiary-color: #9747ff;
		--quaternary-color: #e7e7e7;

		--font-large-text: 4rem/4.8rem 'neue-haas-grotesk-text', sans-serif;
		--font-body-text: 2rem 'Times New Roman';
		--font-small-text: 1.4rem 'Times New Roman';
	}

	:global(body:has(.dark-mode)) {
		--primary-color: #000;
		--secondary-color: #fff;
	}
</style>