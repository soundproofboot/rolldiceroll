<script lang=ts>
	import { onMount } from 'svelte';

    let heads = true;
    let down = true;
    let disabled = true;
    let coinHeight = 200;

    const flip = (flips: number, interval: number) => {
        let count = 0;
        let flipInterval = setInterval(() => {
            if (down) {
                if (coinHeight > 0) coinHeight -= 20;
                else {
                    down = !down;
                    heads = !heads;
                }
            } else {
                if (coinHeight < 200) coinHeight += 20;
                else {
                    down = !down;
                    count++;
                    if (count === flips) clearInterval(flipInterval)
                }
            }
        }, interval);
    }

    onMount(() => {
        setTimeout(() => {
            flip(2, 20);
        }, 250);
        setTimeout(() => {
            disabled = false;
        }, 1000);
    })
</script>
<div class=page>
    <div class=coinContainer>
        <div class=coin style:height={coinHeight}px>
            {#if heads}
            <img src='./favicon.png' class='side svelteIcon' alt='svelte icon'/>
            {:else}
            <img src='./reactIcon.png' class='side reactIcon' alt='react icon'/>
            {/if}
        </div>
    </div>
    <button class=flipButton {disabled} style="background-color: black" on:click={() => flip(Math.random() > .5 ? 10 : 11, 5)}>Flip</button>
</div>
<style>
    .page {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: black;
        height: 100vh;
        width: 100vw;
    }

    .coinContainer {
        height: 200px;
        width: 200px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .coin {
        width: 200px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .side {
        height: 100%;
        width: 100%;
        border-radius: 50%;
    }

    .svelteIcon {
        background-color: white;
        background-color: orangered;
    }

    .reactIcon {
        background-color: black;
    }

    .flipButton {
        margin-top: 5em;
        outline: 1px solid white;
        color: white;
        border-radius: 8px;
        padding: 1em;
        font-size: 1.5em;
        font-weight: bold;
        cursor: pointer;
    }

    .flipButton:disabled {
        opacity: .5;
    }
</style>