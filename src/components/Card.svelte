<script>
    import axios from 'axios';
    import MoreInfo from './MoreInfo.svelte';
    export let name;
    export let url;
    let moreInfo = undefined;
    let error = false;

    async function handleLoadData() {
        try {
            const {data} = await axios.get(url);
        moreInfo = data;
        
        } catch (e) {
            error = e;
        }
    }
</script>

<article>
    <h1>{name}</h1>
    {#if moreInfo === undefined}
    <button on:click={handleLoadData}>Load info</button>
    {:else }
    {#await moreInfo}
        {:then moreInfo}
            {#if moreInfo}
                <MoreInfo moreInfo={moreInfo} />
            {/if}
        {:catch error}
            {#if error}
                <p>There was an error</p>
            {/if}
    {/await}
    {/if}
    
</article>

<style>
    article {
        height: 10em;
    padding: 0.5em;
    background: #fff;
    box-shadow:
        0 5px 10px rgba(0, 0, 0, 0.1),
        0 20px 20px rgba(0, 0, 0, 0.05);
        border-radius: 5px;
    }

    button {
        display: inline-block;
        border-radius: 3px;
        padding: 0.5rem 0;
        margin: 0.5rem 1rem;
        width: 5rem;
        background: transparent;
        color: #ff3e00;
        border: 2px solid #ff3e00;
    }
</style>