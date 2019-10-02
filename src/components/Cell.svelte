<script>
	import { createEventDispatcher } from 'svelte';


    export let element;
    export let isotope = {};
    export let size = 10;

    export let x;
    export let y;

    const dispatch = createEventDispatcher();
    function cellClick() {
            dispatch('cellClick', {
            element,
            isotope
        });
    }
</script>

<style type="text/scss">
    $stable-fill: #00a23b;
    $stable-color: #fff;

    $alpha-fill: #f95354;
    $alpha-color: #fff;

    $betta-fill: #64c0da;
    $betta-color: #fff;

    $neutron-fill: #f93;
    $neutron-color: #fff;

    $unknown-fill: #99afcb;
    $unknown-color: #fff;

    $asd: #fa9d99;
    $asd: #fc0;
    $asd: #8cc63f;
    $asd: #f93;
    $asd: #6b90ca;

    .nuclearCell {
    }

    .cellTitle {
        font-size: 5px;
    }

    rect {
        stroke-width: .5;
        stroke: gray;
    }

    text {
        user-select: none;
    }

    .stable {
        rect { fill: $stable-fill; }
        text { fill: $stable-color; }
    }

    .alpha {
        rect { fill: $alpha-fill; }
        text { fill: $alpha-color; }
    }

    .betta {
        rect { fill: $betta-fill; }
        text { fill: $betta-color; }
    }

    .neutron {
        rect { fill: $neutron-fill; }
        text { fill: $neutron-color; }
    }

    .unknown {
        rect { fill: $unknown-fill; }
        text { fill: $unknown-color; }
    } 
</style>

<g class={`nuclearCell ${isotope.decay.type}`} on:click={cellClick}>
    <rect
        width={size}
        height={size}
        x={x}
        y={y}
    />
    <text 
        class="cellTitle"
        x={x + 2}
        y={y + 2}
        text-anchor="start"
        alignment-baseline="hanging"
    >
        {element.shortTitle}{element.protonsCount + isotope.neutronsCount}
    </text>
</g>
