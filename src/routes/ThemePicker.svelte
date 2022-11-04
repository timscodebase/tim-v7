<script lang="ts">
	import { onMount } from 'svelte';
	let isOpen = false;

	onMount(() => {
		const colorThemes = document.querySelectorAll('[name="theme"]');
		const toggle = document.querySelector('.theme-toggle');
		const fieldset = document.querySelector('fieldset');
		const icon = document.querySelector('p');

		toggle?.addEventListener('click', () => {
			fieldset?.classList.toggle('closed');
			icon?.classList.toggle('spin');
			isOpen = !isOpen;
		});

		const storeTheme = function (theme) {
			localStorage.setItem('theme', theme);
		};

		const setTheme = function () {
			const activeTheme = localStorage.getItem('theme');
			colorThemes.forEach((theme) => {
				if (theme.id === activeTheme) {
					theme.checked = true;
				}
				document.documentElement.className = theme;
			});
		};

		colorThemes.forEach((theme) => {
			theme.addEventListener('click', () => {
				storeTheme(theme.id);
			});
		});

		document.onload = setTheme();
	});
</script>

<form action="" class="color-picker">
	<fieldset class="closed">
		<legend class="sr-only">Choose a theme</legend>
		<div class="theme-toggle" data-tooltip="Change Theme">
			<p class="icon">{isOpen ? '◀️' : 'T'}</p>
		</div>
		<a
			href="https://github.com/timscodebase/My-Past-Site-Versions/blob/main/README.md"
			target="_blank"
			rel="noopener noreferrer nofollow">v7</a
		>
		<label class="sr-only" for="cafe-light">Cafe Light</label>
		<input type="radio" name="theme" id="cafe-light" checked />
		<label class="sr-only" for="cafe-dark">Cafe Dark</label>
		<input type="radio" name="theme" id="cafe-dark" />

		<label class="sr-only" for="true-blood-light">True Blood Light</label>
		<input type="radio" name="theme" id="true-blood-light" />
		<label class="sr-only" for="true-blood-dark">True Blood Dark</label>
		<input type="radio" name="theme" id="true-blood-dark" />

		<label class="sr-only" for="blue-yellow-light">Blue Yellow Light</label>
		<input type="radio" name="theme" id="blue-yellow-light" />
		<label class="sr-only" for="blue-yellow-dark">Blue Yellow Dark</label>
		<input type="radio" name="theme" id="blue-yellow-dark" />

		<label class="sr-only" for="blood-water-light">Blood Water Light</label>
		<input type="radio" name="theme" id="blood-water-light" />
		<label class="sr-only" for="blood-water-dark">Blood Water Dark</label>
		<input type="radio" name="theme" id="blood-water-dark" />

		<label class="sr-only" for="bumble-bee-light">Bumble Bee Light</label>
		<input type="radio" name="theme" id="bumble-bee-light" />
		<label class="sr-only" for="bumble-bee-dark">Bumble Bee Dark</label>
		<input type="radio" name="theme" id="bumble-bee-dark" />
	</fieldset>
</form>

<style>
	.color-picker {
		position: absolute;
		top: 0;
		right: 64px;
	}
	.color-picker > fieldset {
		position: absolute;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		padding: 1rem;
		background: var(--menu-color);
		width: fit-content;
		margin-left: auto;
		will-change: transform;
		transform: translateX(0);
		transition: transform 0.25s ease-in-out;
	}
	.color-picker > fieldset a {
		font-weight: bold;
		text-align: center;
		color: color-contrast(var(--bg-color));
	}

	input {
		position: relative;
	}

	.icon {
		color: color-contrast(var(--bg-color));
		will-change: transform;
		transform: rotate(0deg);
		transition: transform 0.35s ease-in-out;
	}

	.closed {
		transform: translateX(64px) !important;
	}

	.color-picker > fieldset .theme-toggle {
		position: absolute;
		display: grid;
		place-items: center;
		min-width: 16px;
		top: 0;
		left: -47px;
		padding: 1rem;
		background: var(--menu-color);
	}

	.color-picker input[type='radio'] {
		appearance: none;
		width: 1.5rem;
		height: 1.5rem;
		outline: 3px solid var(--radio-color, currentColor);
		outline-offset: 2px;
		border-radius: 50%;
	}

	.color-picker input[type='radio']:checked {
		background: var(--radio-color);
	}

	.color-picker input[type='radio']#cafe-light {
		--radio-color: #c0b7b1;
	}
	.color-picker input[type='radio']#cafe-dark {
		--radio-color: #433e3f;
	}

	.color-picker input[type='radio']#true-blood-light {
		--radio-color: #a29c9b;
	}
	.color-picker input[type='radio']#true-blood-dark {
		--radio-color: #511c29;
	}

	.color-picker input[type='radio']#blue-yellow-light {
		--radio-color: #dab785;
	}
	.color-picker input[type='radio']#blue-yellow-dark {
		--radio-color: #031d44;
	}

	.color-picker input[type='radio']#blood-water-light {
		--radio-color: #73eedc;
	}
	.color-picker input[type='radio']#blood-water-dark {
		--radio-color: #04030f;
	}

	.color-picker input[type='radio']#bumble-bee-light {
		--radio-color: #f2af29;
	}
	.color-picker input[type='radio']#bumble-bee-dark {
		--radio-color: #000000;
	}

	.cafe-light,
	:root:has(#cafe-light:checked) {
		--bg-color: #c0b7b1;
		--text-color: #433e3f;
		--menu-color: #7a7265;
		--hl-color: #c69c72;
		--secondary-hl-color: #7a7265;
		--menu-text-color: var(--text-color);
	}
	.cafe-dark,
	:root:has(#cafe-dark:checked) {
		--bg-color: #433e3f;
		--text-color: #c0b7b1;
		--menu-color: #7a7265;
		--hl-color: #c69c72;
		--secondary-hl-color: #7a7265;
		--menu-text-color: var(--text-color);
	}

	.true-blood-light,
	:root:has(#true-blood-light:checked) {
		--bg-color: #a29c9b;
		--text-color: #511c29;
		--menu-color: #7a7265;
		--hl-color: #c69c72;
		--hl-color: #db324d;
		--secondary-hl-color: #a62639;
		--menu-text-color: var(--bg-color);
	}
	.true-blood-dark,
	:root:has(#true-blood-dark:checked) {
		--bg-color: #511c29;
		--text-color: #a29c9b;
		--menu-color: #7a7265;
		--hl-color: #c69c72;
		--hl-color: #db324d;
		--secondary-hl-color: #a62639;
		--menu-text-color: var(--bg-color);
	}

	.blue-yellow-light,
	:root:has(#blue-yellow-light:checked) {
		--bg-color: #dab785;
		--text-color: #031d44;
		--menu-color: #04395e;
		--hl-color: #d5896f;
		--secondary-hl-color: #70a288;
		--menu-text-color: var(--bg-color);
	}
	.blue-yellow-dark,
	:root:has(#blue-yellow-dark:checked) {
		--bg-color: #031d44;
		--text-color: #dab785;
		--menu-color: #04395e;
		--hl-color: #70a288;
		--secondary-hl-color: #d5896f;
		--menu-text-color: var(--bg-color);
	}

	.blood-water-light,
	:root:has(#blood-water-light:checked) {
		--bg-color: #73eedc;
		--text-color: #04030f;
		--menu-color: #776885;
		--hl-color: #5f1a37;
		--secondary-hl-color: #73c2be;
		--menu-text-color: var(--bg-color);
	}
	.blood-water-dark,
	:root:has(#blood-water-dark:checked) {
		--bg-color: #04030f;
		--text-color: #73eedc;
		--menu-color: #776885;
		--hl-color: #73c2be;
		--secondary-hl-color: #5f1a37;
		--menu-text-color: var(--bg-color);
	}

	.bumble-bee-light,
	:root:has(#bumble-bee-light:checked) {
		--bg-color: #f2af29;
		--text-color: #000000;
		--menu-color: #474747;
		--hl-color: #e0e0ce;
		--secondary-hl-color: #ad343e;
		--menu-text-color: var(--bg-color);
	}
	.bumble-bee-dark,
	:root:has(#bumble-bee-dark:checked) {
		--bg-color: #000000;
		--text-color: #f2af29;
		--menu-color: #474747;
		--hl-color: #ad343e;
		--secondary-hl-color: #e0e0ce;
		--menu-text-color: var(--bg-color);
	}
</style>
