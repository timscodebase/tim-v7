<script>
	import ThemePicker from './ThemePicker.svelte';
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<ThemePicker />
	<Header />

	<main>
		<slot />
	</main>

	<footer>Tim Smith</footer>
</div>

<style>
	.app {
		position: relative;
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
		color: color-contrast(var(--bg-color));
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
