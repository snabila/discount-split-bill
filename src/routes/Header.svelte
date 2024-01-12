<script>
	import { page } from '$app/stores';
	import logo from '$lib/images/svelte-logo.svg';
	import github from '$lib/images/github.svg';
</script>

<header>
	<div>
		<h1>
			Discount Calculator
		</h1>
	</div>
	<nav>
		<ul>
			<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">Home</a>
			</li>
			<li aria-current={$page.url.pathname === '/about' ? 'page' : undefined}>
				<a href="/about">About</a>
			</li>
			<li class="git">
				<a href="https://github.com/snabila/discount-split-bill">
					<img src={github} alt="GitHub" />
				</a>
			</li>
		</ul>	
	</nav>
</header>

<style>

	h1 {
		font-size: 18px;
		width: 100%;
		font-weight: 600;
		text-transform: uppercase;
		letter-spacing: 0.1em;
	}
	
	header {
		display: flex;
		justify-content: space-between;
		padding-bottom: 48px;
	}

	header div {
		display: flex;
		align-items: center;
	}

	.git {
		width: 3em;
		height: 3em;
	}

	nav {
		display: flex;
		justify-content: center;
	}

	ul {
		margin: 0;
		display: flex;
		list-style: none;
		align-items: center;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
