<script>
    import Empty from "./Empty.svelte";
    import Book from "./Book.svelte";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    export let list = [];

    function addToCart({ detail }) {
        dispatch('add-cart', detail);
    }
</script>

<style>
    section {
        padding: 1rem;
        margin: 1rem 0;
        border-radius: 10px;
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.265);
    }
</style>

{#if list && list.length}
    {#each list as book}
        <section>
            <Book info={book} on:add-cart={addToCart} />
        </section>
    {/each}
{:else}
    <Empty>书架空空如也</Empty>
{/if}
