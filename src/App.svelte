<script>
	import Tailwindcss from './Tailwindcss.svelte';
	import Song from './song.svelte';

	export let name;

	const songs = fetch('https://itunes.apple.com/us/rss/topalbums/limit=100/json')
		.then((result) => {return result.json();})
		.then((data) => {
			console.log(data.feed.entry[0])
			return data.feed.entry;
		})
		.catch(err => console.log(err))
</script>

<Tailwindcss />
<main class="flex flex-wrap justify-center">
	{#await songs}
		<p>waiting ...</p>
	{:then songss}
		{#each songss as song}
			<div>
				<Song {song}/>
			</div>
		{/each}
	{:catch error}
		<p style="color: red;">{error.message}</p>
	{/await}
</main>

<style>
	main{
		max-width: 1200px;
		margin: 0 auto;
	}
</style>
