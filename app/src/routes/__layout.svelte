<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
	import { afterUpdate } from 'svelte';

	let show = false;

	afterUpdate(() => {
		show = true;
	});
</script>

<Header />

<main class="">
	<slot />
</main>

{#if show}
	<footer class="footer footer-center p-4 bg-base-300 text-base-content rounded-box">
		<div>
		  <p>Copyright © 2022 - All right reserved by none</p>
		</div>
	</footer>
{/if}

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 40px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
