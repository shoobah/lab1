<script>
	import Bar from '$lib/Bar.svelte';
	import { onMount } from 'svelte';

	let val = 1;
	let numberOfBars = 10;

	$: values = Array(numberOfBars).fill(400);

	/**
	 * @param {number} min
	 * @param {number} max
	 */
	function random(min, max) {
		val = Math.round(Math.random() * (max - min) + min);
		return val;
	}

	function randomColor() {
		return `#${Math.floor(Math.random() * 16777215).toString(16)}`;
	}

	function randomBars() {
		values = values.map(() => random(1, 1000));
	}

	onMount(() => {
		randomBars();
	});
</script>

<button on:click={randomBars}>Randomize</button>
<input type="range" bind:value={numberOfBars} min="5" max="500" on:change={randomBars} />
<br />

{#each values as value}
	<Bar {value} width={1000} height={1000 / numberOfBars} color={randomColor()} />
{/each}
<div />

<style>
	button {
		background-color: #6553b2;
		color: #f1ffb7;
		border: none;
		border-radius: 5px;
		padding: 10px;
		font-size: 16px;
		cursor: pointer;
	}
</style>
