<script>
	import { page } from '$app/stores';
</script>

<header>
	<div class="corner">
		<a href="/"> Tim Smith </a>
	</div>

	<nav>
		<ul>
			<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">Me</a>
			</li>
			<li aria-current={$page.url.pathname === '/projects' ? 'page' : undefined}>
				<a href="/projects">Projects</a>
			</li>
			<li aria-current={$page.url.pathname === '/resume' ? 'page' : undefined}>
				<a href="/resume">Resume</a>
			</li>
			<li aria-current={$page.url.pathname === '/uses' ? 'page' : undefined}>
				<a href="/uses">Uses</a>
			</li>
		</ul>
	</nav>
	<div />
</header>

<style>
	header {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		background: var(--text-color);
		padding: 3rem 1rem;
	}

	header a {
		color: var(--bg-color);
		text-decoration: none;
	}

	nav ul {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
	}
</style>
