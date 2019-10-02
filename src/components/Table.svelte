<script>
    import Row from './Row.svelte';
    import {CELL_HEIGHT} from '../models/constants';

    /** Коэффициент масштабирования */
    export let scale;
    /** Центр */
    export let center;
    /** */
    export let direction;
    export let data;

    const MAX_PROTONS_COUNT = 118;
    const MAX_NEUTRONS_COUNT = 61;
    
    $: viewBox = `${center.x} ${center.y} ${scale * CELL_HEIGHT * data.length} ${scale * CELL_HEIGHT * MAX_NEUTRONS_COUNT}`;
</script>

<style>
    .nuclearTable {
        width: 100%;
        height: 100%;
    }
</style>

<svg
    class="nuclearTable"
    xmlns="http://www.w3.org/2000/svg"
    {viewBox}
    preserveAspetRatio="none"
>
    {#each data as element}
        <Row
            {direction}
            {element}
            on:cellClick
        />
    {/each}
</svg>