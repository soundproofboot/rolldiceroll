<script lang=ts>
    import { page } from "$app/stores";
    $: route = $page.route.id;
</script>

<nav>
    <a href='/' class={route === '/' ? 'selected' : ''}>ROLL</a>
    <a href='/coinflip' class={route === '/coinflip' ? 'selected' : ''}>FLIP</a>
</nav>
<slot></slot>

<style>
    :global(body) {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Arial';
    }

    nav {
        position: absolute;
        color: white;
        display: flex;
        justify-content: space-evenly;
        width: 100%;
    }
    nav a {
        padding: 20px 0;
        width: 50%;
        text-align: center;
        text-decoration: none;
        color: white;
        background-color: rgb(141, 141, 141);
    }
    
    .selected {
        outline: 1px solid white;
        text-shadow: 0 0 2px black;
        font-size: large;
    }

    a:not(.selected) {
        background-color: lightgray;
    }
</style>