<script>
    export let results;

    console.log(results)
</script>
<h4>Results</h4>
{#if results.length > 0}
    {#each results as spinResult, i}
        <img 
            alt={spinResult.src} 
            src={spinResult.src} 
            style:background={spinResult.colour}
            style:transform="scaleX({spinResult.scale})"
        />
    {/each}
{/if}

<style>
    img {
        width: 30px;
        height: 30px
    }
</style>