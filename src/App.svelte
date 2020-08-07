<script>
    import Books from "./components/Books.svelte";
    import Add from "./components/Add.svelte";
    import Cart from "./components/Cart.svelte";

    let books = [];
    let cartItems = [];

    function onAddNewBook({ detail }) {
        books = books.concat(detail);
    }

    function onAddToCart({detail}) {
        cartItems = cartItems.concat(detail);
    }
</script>

<style>
    main {
        max-width: 750px;
        margin: auto;
    }
    .wrapper {
        display: flex;
    }
    .books {
        flex: 2;
        padding-right: 1em;
        margin-right: 1em;
        border-right: 1px dashed #bfbfbf;
    }
    .cart {
        flex: 1;
    }
</style>

<main>
    <Add on:add={onAddNewBook} />
    <div class="wrapper">
        <div class="books">
            <Books list={books} on:add-cart={onAddToCart} />
        </div>
        <div class="cart">
            <Cart list={cartItems} />
        </div>
    </div>
</main>
