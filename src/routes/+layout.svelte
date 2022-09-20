<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />

<main class=" flex bg-sky-100 dark:bg-sky-800 ">
	<slot />
</main>

<footer class="bg-sky-700 ">
	<p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p>
</footer>
