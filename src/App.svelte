<script>
	import nuclearData from './models/nuclearTableData15';

	import Fotter from './components/Fotter.svelte'

	import Table from './components/Table.svelte';
	import IsotopeDetails from './components/IsotopeDetails.svelte';

	let direction = 'row'; // 'row' | 'column'
	let center = {x: 0, y: 0};
	let scale = 1;
	let isDragging = false;

	let selectedElement = nuclearData[0];
	let selectedIsotope = nuclearData[0].isotopes[0];

	function expand(e) {
		const coef = 0.05;
		center.x -= scale * e.offsetX * coef;
		center.y -= scale * e.offsetY * coef;
		scale = scale / 1.3;
	}

	function startDrag() {
		isDragging = true;
	}

	function dragHandler(e) {
		if (isDragging) {
 			center.x -= e.movementX * 2.5;
			center.y -= e.movementY * 2.5;
		}
	}

	function endDrag() {
		isDragging = false;
	}

	function onCellClick(event) {
		selectedElement = event.detail.element;
		selectedIsotope = event.detail.isotope;
	}

	function toggleDirection(event) {
		direction = event.detail.direction;
	}
</script>


<style>
	h1 {
		color: purple;
	}
	.content {
		height: 50vh;
		width: 98vw;
		overflow: scroll;

		position: relative;

		border: 1px solid black;
	}
</style>


<div class="content"
	on:dblclick={expand}
	on:mousedown={startDrag}
	on:mousemove={dragHandler}
	on:mouseup={endDrag}
	on:mouseleave={endDrag}	
> 
	<Table
		data={nuclearData}
		{direction}
		{center}
		scale={scale}
		on:cellClick={onCellClick}
	/>

	{#if selectedElement && selectedIsotope}
		<IsotopeDetails element={selectedElement} isotope={selectedIsotope} />
	{/if}
</div>


<Fotter
	bind:scale={scale}
	{direction}
	on:directionToggle={toggleDirection}
 />
