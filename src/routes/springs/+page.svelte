<script>
	import Bar from '$lib/Bar.svelte';
	import { onMount } from 'svelte';

	let val = 1;
	let numberOfBars = 10;

	/**
	 * @param {any} length
	 */
	function randomArray(length) {
		return Array.from({ length }, () => random(1, 1000));
	}

	$: values = randomArray(numberOfBars);

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

	function generateLightColorHex() {
		let color = '#';
		for (let i = 0; i < 3; i++)
			color += ('0' + Math.floor(((1 + Math.random()) * Math.pow(16, 2)) / 2).toString(16)).slice(
				-2
			);
		return color;
	}

	function randomBars() {
		values = values.map(() => random(1, 1000));
	}

	onMount(() => {
		randomBars();
	});
</script>

<button on:click={randomBars}>Randomize</button>
<input type="range" bind:value={numberOfBars} min="5" max="500" />
<span>{numberOfBars}</span>
<br />

{#each values as value}
	<Bar
		{value}
		width={1000}
		height={500 / numberOfBars}
		color={generateLightColorHex()}
		showText={numberOfBars < 26}
	/>
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
