<script>
    import Empty from "./Empty.svelte";

    export let list = [];

    $: totalPrice = list.reduce((total, book) => total + book.price * 1, 0);
</script>

<style>
    section {
        padding: 1rem;
        margin: 1rem 0;
        border-radius: 10px;
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.265);
    }
    ul {
        margin: 0;
        padding: 0;
        width: 100%;
        list-style: none;
    }
    .info {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    span {
        font-size: 1.25rem;
        color: #020822;
    }
    footer {
        padding-top: 0.5em;
        margin-top: 0.5em;
        color: #020822;
        font-size: 1.25rem;
        font-weight: bold;
        text-align: right;
        border-top: 1px solid #bfbfbf;
    }
</style>

{#if list && list.length}
    <section>
        <ul>
            {#each list as book}
                <li class="info">
                    <span>{book.title}</span>
                    <span>${book.price}</span>
                </li>
            {/each}
        </ul>
        <footer class="info">
            <span>合计</span>
            <span>${totalPrice}</span>
        </footer>
    </section>
{:else}
    <Empty>购物车空空如也</Empty>
{/if}
