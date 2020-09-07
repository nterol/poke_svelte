<script>
    let count = 0;
    const handleClick = () => {
        count++;
    }

    $:console.log("👑", count)
</script>

<button on:click={handleClick}>Click me !</button>
<p>{count} clique{count <=  1 ? '' : 's'}</p>

<style>
    button {
        display: inline-block;
        border-radius: 3px;
        padding: 0.5rem 0;
        margin: 0.5rem 1rem;
        width: 11rem;
        background: transparent;
        color: #ff3e00;
        border: 2px solid #ff3e00;
    }
</style>