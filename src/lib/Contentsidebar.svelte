<script type='ts'>
	import Contentsection from './Contentsection.svelte';
	export let articles;
	export let layout;
</script>

<div class="content">
	<div>
		<Contentsection {articles} {layout}/>
	</div>
	<div><div>my right section</div></div>
</div>

<style>
	.content {
		display: grid;
		grid-column-gap: calc(1rem * 2 + 1px);
		grid-template-columns: repeat(20, 1fr);
	}

	.content > div:first-child {
		grid-column: 1/15;
		background-color: orange;
	}

	.content > div:last-child {
		grid-column: 15/21;
		background-color: grey;
		position: relative;
	}

	.content > div:last-child::before {
		content: '';
		height: 100%;
		position: absolute;
		left: calc(-1rem - 1px);
		border-left: 1px solid var(--color-stroke-tertiary);
	}

	@media only screen and (max-width: 1069px){
		.content {
			display: block;
		}
	}

</style>