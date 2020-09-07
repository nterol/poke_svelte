<script>
	import List from './components/List.svelte'	
	const name = "<strong>Nicolas</strong>";
	const src = 'https://picsum.photos/900/300'
	let imgStatus = false;


	const img1 = new Image();
	img1.src = src;

	img1.onload = () => imgStatus = true;
</script>


	<header>
		{#if imgStatus}
			<img {src}  alt="header image" />
		{:else}
			<div class="card" ></div>
		{/if}
		<h1>Hello {@html name}!</h1>
	</header>
	<main>
		<List />
	</main>

<style>
	header {
		text-align: center;
	}

	main {
		border: 1px solid black;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;	
	}

	.card {
		background: lightgray;
		height: 300px;
		width: 900px;
		border-radius: 4px;
		margin: 0 auto;
	}

	img {
		border-radius: 4px;
		
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 812px) {
		main {
			max-width: none;
		}
	}
</style>