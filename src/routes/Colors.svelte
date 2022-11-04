<div class="colors">
	<div />
	<div />
	<div />
	<div />
	<div />
</div>

<style>
	.colors {
		width: 100%;
		margin: 1rem;
		display: flex;
		border: 1px solid var(--text-color);
	}

	.colors div {
		flex: 1;
		height: 60vh;
	}

	.colors div:nth-child(1) {
		background: var(--bg-color);
	}

	.colors div:nth-child(2) {
		background: var(--text-color);
	}

	.colors div:nth-child(3) {
		background: var(--menu-color);
	}

	.colors div:nth-child(4) {
		background: var(--hl-color);
	}

	.colors div:nth-child(5) {
		background: var(--secondary-hl-color);
	}
</style>
