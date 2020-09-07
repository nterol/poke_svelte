<script>
let fibo = [1, 2];
    const handleFibo = () => {
        const n = fibo[fibo.length - 2] + fibo[fibo.length - 1];
        fibo = [...fibo, n]
    }

    $:console.log("🧮", fibo);
</script>

<button on:click={handleFibo}>Fibo !</button>

<p>{fibo[fibo.length -1]}</p>

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