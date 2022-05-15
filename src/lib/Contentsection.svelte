<script>
	import Articlessingle from './Articlessingle.svelte';
	import Articlesdouble from './Articlesdouble.svelte';
	import Articlestriple from './Articlestriple.svelte';
	import Articlesquadruple from './Articlesquadruple.svelte';

	export let articles;

	// function generateRandomNumber() {
	// 	return Math.floor(Math.random() * 4 + 1);
	// }
</script>

{#if articles}
		<div>
			<Articlesquadruple articles={articles.slice(0,4)} />
		</div>
		<div>
			<Articlestriple articles={articles.slice(0, 3)} />
		</div>
		<div>
			<Articlesdouble articles={articles.slice(0, 2)} />
		</div>
		<div>
			<Articlessingle articles={articles[0]} />
		</div>
{/if}

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
