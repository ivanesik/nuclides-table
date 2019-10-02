<script>
    export let element;
    export let isotope;
</script>


<style lang="scss">
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

    .notation {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        position: absolute;

        top: 0;
        right: 0;

        width: 80px;
        height: 100px;

        padding: 5px;

        border-radius: 5px;

        font-weight: bold;
    }

    .stable {
        background-color: $stable-fill;
        color: $stable-color;
    }

    .alpha {
        background-color: $alpha-fill;
        color: $alpha-color;
    }

    .betta {
        background-color: $betta-fill;
        color: $betta-color;
    }

    .neutron {
        background-color: $neutron-fill;
        color: $neutron-color;
    }

    .unknown {
        background-color: $unknown-fill;
        color: $unknown-color;
    } 
</style>


<div class="notation {isotope.decay.type}" >
    <div>
        <div>
            {`${element.shortTitle}${element.protonsCount + isotope.neutronsCount}`}
        </div>
        <div>
            {element.title}
        </div>
    </div>
    <div>{isotope.decay.title}</div>
</div>