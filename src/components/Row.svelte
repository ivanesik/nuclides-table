<script>  
    import Cell from './Cell.svelte';
    import {CELL_HEIGHT} from '../models/constants';

    export let direction;
    export let element;
    export let row = {};

    $: cellX = (isotope) => direction === 'row' ? isotope.neutronsCount : element.protonsCount;
    $: cellY = (isotope) => direction === 'row' ? element.protonsCount : isotope.neutronsCount;

</script>


<g>
    {#each element.isotopes as isotope, index}
        <Cell
            {element}
            {isotope}
            size={CELL_HEIGHT}
            x={cellX(isotope) * CELL_HEIGHT}
            y={cellY(isotope) * CELL_HEIGHT}
            on:cellClick
        />
    {/each}
</g>