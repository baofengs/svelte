<script>
    import Button from "./Button.svelte";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    export let info = {};

    function onAddToCart() {
        dispatch('add-cart', info);
    }
</script>

<style>
    h1 {
        margin: 1rem 0;
        font-size: 1.5rem;
        color: #020822;
        font-weight: bold;
    }
    h2 {
        margin: 1rem 0;
        font-size: 1.25rem;
    }
    p {
        font-size: 1rem;
    }
    footer {
        text-align: right;
    }
</style>

<h1>{info.title}</h1>
<h2>${info.price}</h2>
<p>{info.desc}</p>
<footer>
    <Button on:click={onAddToCart}>加入购物车</Button>
</footer>
