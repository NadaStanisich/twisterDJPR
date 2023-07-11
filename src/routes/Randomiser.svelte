<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    let sides = ["Left", "Right"];
    let bodyParts = ["Hand", "Foot"];
    let colours = ["Red", "Blue", "Yellow", "Green"];
    let spinResult;
    let src;
    let scale;

    function handleSpinButton() {
        spin();
        dispatchSpin();
    }

    function dispatchSpin() {
        dispatch('spin', 
            {
                spinResult
            }
        );
    }

    function spin() {
        let side = getRandom(sides);
        let bodyPart = getRandom(bodyParts);;
        let colour = getRandom(colours);

        spinResult = {
            side,
            bodyPart,
            colour
        }

        bodyPart === "Foot" ? src = '/img/Foot.png': src = '/img/Hand.png';
        side === "Left" ? scale = 1 : scale = -1;

        return spinResult;
    }

    function getRandom(array) {
        return array[Math.floor(Math.random() * array.length)];
    }
</script>
<div>
<button on:click={handleSpinButton}>Spin!</button>
<div id='spinner'>
    {#if spinResult}
    <div class='display' style:background={spinResult.colour} >
        <img {src} alt="body part" style:transform="scaleX({scale})" />
        
    </div>
    <div>
        { spinResult.side } { spinResult.bodyPart} { spinResult.colour }
    </div>
    {/if}
</div>
</div>

<style>
    div {
        text-align: center;
    }
    .display {
        width: 50px;
        height: 50px;
        border: 1px solid black;
        margin: auto;
    }

    img {
        width: 50px;
        height: 50px;
    }
</style>