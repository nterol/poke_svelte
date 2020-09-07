<script>
import axios from 'axios';
import Card from './Card.svelte';
let error = false;
const getPokemon = async () => {
    try {
        const {data} = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=151'); 
    return data;
    } catch (e) {
        error = e;
    }
}
let pokemons = getPokemon();

</script>

<section>
    <h1>Pokemons</h1>
    <div class="grid">
        {#await pokemons}
            <p>Loading pokemon</p>
        {:then pokemons } 
            {#each pokemons.results as pokemon}
                <Card {...pokemon} />
            {/each}
        {/await}
    </div>
</section>


<style>
    section {
        
        margin-top: 32px;
        max-width: 90%;
        
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        grid-gap: 1em;
    }
</style>