<script>
	import Header from './Header.svelte';
	import './styles.css';
	import './fonts.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>
</div>

<style>
	* {
		font-family: 'Lora', sans-serif;
	}

	.app {
		width: 90vw;
		max-width: 1000px;
		min-height: 100vh;
		margin: 24px auto;
	}

	main {
		width: 100%;
		box-sizing: border-box;
	}
</style>
