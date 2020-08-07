<script>
    import Button from "./Button.svelte";
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let id = 0;
    let title = "";
    let price = "";
    let desc = "";

    function onSubmit(e) {
        const {target} = e;
        const book = ["title", "price", "desc"].reduce((acc, key) => {
            acc[key] = target[key].value;
            return acc;
        }, {id});
        dispatch("add", book);
        id++;
        target.reset();
    }
</script>

<style>
     form {
        padding: 1rem;
        margin: 1rem 0;
        border-radius: 10px;
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.265);
    }
    p {
        display: flex;
        align-items: center;
    }
    label {
        width: 4em;
        text-align: right;
        margin-right: 0.5rem;
    }
    input,
    textarea {
        flex: 1;
        margin: 0;
    }
    footer {
        text-align: right;
    }
</style>

<form on:submit|preventDefault={onSubmit} >
    <p>
        <label for="title">标题:</label>
        <input id="title" name="title" required type="text" value={title} />
    </p>
    <p>
        <label for="price">价格:</label>
        <input id="price" name="price" required type="number" step="0.01" value={price} />
    </p>
    <p>
        <label for="desc">描述:</label>
        <textarea id="desc" name="desc" rows="3" value={desc} />
    </p>
    <footer>
        <Button type="submit">新增</Button>
    </footer>
</form>
