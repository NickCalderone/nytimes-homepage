<script>
	import Contentsidebar from '../lib/Contentsidebar.svelte';

	async function getHomepageArticles() {
		const response = await fetch(
			'https://api.nytimes.com/svc/topstories/v2/home.json?api-key=GxINPsIPrAO6UJucICIvNPAzrgb2ourt'
		);
		const data = await response.json();

		if (response.ok) {
			console.log('working');
			console.log(data);
			return data.results;
		} else {
			throw new Error(data);
		}
	}

	let homepageArticles = getHomepageArticles();

</script>

{#await homepageArticles}
	<p>Loading</p>
{:then articles}
	<Contentsidebar articles={articles} />
	{#each articles as { title, url, multimedia, byline }}
	<p>{title}</p>
	{/each}
	<h1>Welcome to SvelteKit</h1>
	<p>first article is {articles[10].title}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

<!-- {#each feed['results'] as abstract}
	<p>{abstract.title}</p>
{/each} -->

<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<style>
	main {
		height: 100%;
	}
</style>