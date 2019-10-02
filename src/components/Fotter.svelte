<script>
	import { createEventDispatcher } from 'svelte';

	export let scale;
    export let direction;


	const dispatch = createEventDispatcher();
    function onDirectionToggle() {
		dispatch('directionToggle', {
			direction: direction === 'row' ? 'column' : 'row'
		});
    }
</script>


<footer>
	<div>
		<span>Search element:&nbsp;</span>
		<input type="text"/>
	</div>
	<div>
		<span>View type:&nbsp;</span>
		<select>
			<option>Decay</option>
			<option>T/2-period</option>
			<option>3</option>
			<option>4</option>
		</select>
	</div>

	<div>
		<button on:click={onDirectionToggle}>{direction}</button>
	</div>

	<div>
		<span>Scale:&nbsp;</span>
		<input type="range" bind:value={scale} min="0" max="3" step={0.05}>
	</div>

</footer>