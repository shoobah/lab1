<script>
	import { spring } from 'svelte/motion';

    /** @type {number} */
    export let value;

    /** @type {string} */
    export let color="#beafff";

    /** @type {number} */
    export let width=1000;
    export let height=10;

    export let showText=false

    export let border=false;

	const val = spring(1, { stiffness: 0.5, damping: 1 });
	$: $val = Math.abs(value);
</script>

<svg viewBox={`0 0 ${width} ${height}`} xmlns="http://www.w3.org/2000/svg" style={`--width:${width}px`}>
	<g>
		<rect x="0" y="0" width={$val} height={height} fill={color} />
        {#if border}
		<rect
			x="0"
			y="0"
			width="1000"
			height="22"
			fill="transparent"
			stroke="#000"
			stroke-width="1"
		/>
        {/if}
        {#if showText}
		<text class="small" x="5" y="17">
			{Math.round($val)}
		</text>
        {/if}
	</g>
</svg>

<style>
	svg {
		width: var(--width);
	}

	.small {
		font: sans 10px sans-serif;
		color: black;
	}
</style>
