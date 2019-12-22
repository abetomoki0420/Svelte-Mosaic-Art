<script>
	import Rectangle  from './Rectangle.svelte'
	import { fade } from 'svelte/transition'

	let message = "hello"
	let hoveredColor = "hover color panel"
	let size = { length: 20}

	function getRandom(max){
		return Math.round(Math.random() * max)
	}

	function getRandomColor(){
		const R = getRandom(255)
		const G = getRandom(255)
		const B = getRandom(255)
		return `rgba(${R},${G},${B},0.4)`
	}

	function showHoveredColor(event){
		hoveredColor = event.detail
	}

</script>

<div class="app">
	<div class="container">
	<h1>Mosaic Art By Svelte</h1>
	<h2 >Color: <span transition:fade> { hoveredColor }</span></h2>
	{#each size as _ }
		<div class="row">
			{#each size as _}
				<Rectangle color={ getRandomColor() } on:notify={ showHoveredColor }/>
			{/each }
		</div>
	{/each }
	</div>
</div>

<style>
.app {
	font-family: "Impact";
	height: 100vh;
	width: 100vw;
	background: rgba(0,0,0,0.1);
}

.container {
	width: 50vw;
	margin: 0 auto ;
}

.row {
	display: flex;
}

</style>
