
<script>
    export let type = 'button';
</script>

<style>
    button {
        margin: 0;
        padding: .25em 1em;
        color: #fff;
        border: 0;
        background-color: #ff1e45;
    }
    button:hover,
    button:active {
        cursor: pointer;
        box-shadow: 1px 5px 10px -5px rgba(0, 0, 0, .265);
    }
</style>

<button type="{type}" on:click>
    <slot />
</button>
