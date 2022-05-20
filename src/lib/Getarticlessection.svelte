<script>

	import Articlessingle from './Articlessingle.svelte'	
	import Articlesdouble from './Articlesdouble.svelte'	
	import Articlestriple from './Articlestriple.svelte'	
	import Articlesquadruple from './Articlesquadruple.svelte'	

	export let articles;

	let length = articles.length

</script>

{#if length == 1}
<Articlessingle {articles} />
{:else if length == 2}
<Articlesdouble {articles} />
{:else if length == 3}
<Articlestriple {articles} />
{:else}
<Articlesquadruple {articles} />
{/if}