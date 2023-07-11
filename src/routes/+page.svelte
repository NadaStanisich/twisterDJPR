<script>
    import Randomiser from "./Randomiser.svelte";
    import ResultDisplay from "./ResultDisplay.svelte";

    let results = []

    function handleSpin(event) {
        //results.push(event.detail.spinResult);
        console.log(event.detail)
        let scale = event.detail.spinResult.side === "Left" ? 1 : -1;
        let result = {
            src: '/img/' + event.detail.spinResult.bodyPart +'.png',
            scale: scale,
            colour: event.detail.spinResult.colour

        }

        results = [...results, result]
        console.log(results)
    }
</script>

<div>
<h1>Twister</h1>
</div>

<Randomiser on:spin={handleSpin}/>
<hr>
<ResultDisplay results={results}/>

<style>
    div {
        text-align: center;
    }
</style>