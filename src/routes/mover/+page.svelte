<script>
	import { spring } from 'svelte/motion';

	const springConfig = { stiffness: 0.8, damping: 0.8 };

	function generateLightColorHex() {
		let color = '#';
		for (let i = 0; i < 3; i++)
			color += ('0' + Math.floor(((1 + Math.random()) * Math.pow(16, 2)) / 2).toString(16)).slice(
				-2
			);
		return color;
	}

	let x = spring(50, springConfig);
	let y = spring(50, springConfig);
	let r = spring(10, { stiffness: 0.5, damping: 0.2 });
	let color = generateLightColorHex();

	/**
	 * @param {{ offsetX: number; offsetY: number; }} e
	 */
	function move(e) {
		$x = e.offsetX;
		$y = e.offsetY;
	}

	function changeSize() {
		$r = Math.random() * 100;
		color = generateLightColorHex();
	}
</script>

<h1 class="text-2xl">Hello world!</h1>
<div class="bg-red-100 p-4 rounded-lg">
	<svg on:click={changeSize} on:mousemove={move}>
		<g>
			<circle cx={$x} cy={$y} r={Math.abs($r)} fill={color} />
		</g>
	</svg>
</div>

<style>
	svg {
		width: 600px;
		height: 600px;
		background-color: rgb(43, 43, 43);
		cursor: none;
		border: solid 2px #6553b2;
		margin: 0 auto;
	}
</style>
