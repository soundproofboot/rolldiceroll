<script lang=ts>
    import One from "../lib/One.svelte"
    import Two from "../lib/Two.svelte"
    import Three from "../lib/Three.svelte"
    import Four from "../lib/Four.svelte"
    import Five from "../lib/Five.svelte"
    import Six from "../lib/Six.svelte"
    import Unknown from "../lib/Unknown.svelte"

    const sideArray = [One, Two, Three, Four, Five, Six];

    const rollDie = (num: number) => {
        return Math.ceil(Math.random() * num)
    }
    const roll = () => {
        let interval = setInterval(() => {
            result = rollDie(6)
        }, 10);
        setTimeout(() => {
            clearInterval(interval)
        }, 500)
    }

    let result: number;
  
</script>
<div class=page>
{#if !result}
<Unknown></Unknown>
{:else}
<svelte:component this={sideArray[result -1]}/>
{/if}
    <button class=rollButton style="background-color: black"on:click={roll}>Roll</button>
</div>

<style>
    :global(body) {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Arial'
    }

    .page {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: black;
        height: 100vh;
        width: 100vw;
    }

    .rollButton {
        margin-top: 5em;
        outline: 1px solid white;
        color: white;
        border-radius: 8px;
        padding: 1em;
        font-size: 1.5em;
        font-weight: bold;
    }
</style>