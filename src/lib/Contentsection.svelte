<script>
	import Articlessingle from './Articlessingle.svelte';
	import Articlesdouble from './Articlesdouble.svelte';
	import Articlestriple from './Articlestriple.svelte';
	import Articlesquadruple from './Articlesquadruple.svelte';

	export let articles = [];

	export let layout = [];
</script>

{#await articles then myArticles}
	{#await layout then myLayout}
		{#each myLayout as section}
			{#if section[1] - section[0] == 1}
				<div>
					this is a single article section
					<!-- <Articlessingle articles={myArticles.slice(section[0], section[1])} /> -->
				</div>
			{:else if section[1] - section[0] == 2}
				<div>
					<Articlesdouble articles={myArticles.slice(section[0], section[1])} />
				</div>
			{:else if section[1] - section[0] == 3}
				<div>
					<Articlestriple articles={myArticles.slice(section[0], section[1])} />
				</div>
			{:else if section[1] - section[0] == 4}
				<div>
					<Articlesquadruple articles={myArticles.slice(section[0], section[1])} />
				</div>
			{/if}
		{/each}
	{/await}
{/await}

<!-- <Getarticlessection articles={articles.slice(0,4)} />
		<div>
			<Articlesquadruple articles={articles.slice(6,11)} />
		</div>
		<div>
			<Articlestriple articles={articles.slice(3, 6)} />
		</div>
		<div>
			<Articlesdouble articles={articles.slice(1, 3)} />
		</div>
		<div>
			<Articlessingle articles={articles[0]} />
		</div> -->
<style>
	div {
		padding-bottom: 1.5rem;
	}

	div::before {
		content: '';
		display: block;
		margin-bottom: 1.25rem;
		border-bottom: 1px solid var(--color-stroke-primary);
	}

	div:last-child {
		padding-bottom: 0;
	}
</style>
