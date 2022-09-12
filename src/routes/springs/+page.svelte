<script>
	import Bar from '$lib/Bar.svelte';

	let val = 1;
	let values = Array(100).fill(10);

	/**
	 * @param {number} min
	 * @param {number} max
	 */
	function random(min, max) {
		val = Math.round(Math.random() * (max - min) + min);
		return val;
	}

    function randomColor() {
        return `#${Math.floor(Math.random()*16777215).toString(16)}`;
    }

	function randomBars() {
		values = values.map(() => random(1, 1000));
	}
</script>

<button on:click={randomBars}>Random</button>
<br />

{#each values as value}
	<Bar {value} width={1000} height={10} color={randomColor()}/>
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
