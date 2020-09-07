<script>
    export let moreInfo;
    
    const { sprites } = moreInfo;

    
</script>

<section class="container">
    More Info
    <div class="category">
    {#each Object.values(sprites).reverse() as sprite}
        {#if !sprite}
            <span class="no-sprite">bite</span>
        {:else}
            <img height="30px" width="30px" src={sprite} alt="front sprite default" />
        {/if}
    {/each}
    </div>
</section>

<style>
    .container {
        border: 1px solid blue;
    }

    .category {
        display : flex;
    }

    .no-sprite {
        width: 10px;
        height: 10px;
        border-radius: 50% 50%;
        background: lightgray;
        border: 1px solid grey;
    }
    
</style>