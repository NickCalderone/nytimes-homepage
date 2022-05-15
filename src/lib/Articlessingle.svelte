<script>
	export let articles;
</script>

<div class="content-article-wrapper">
	<section>
		<h3>{articles.title}</h3>
		<p>{articles.abstract}</p>
	</section>
	<div>
		<img src={articles.multimedia[1].url} />
	</div>
</div>

<style>
	h3 {
		margin: 0px
	}

	.content-article-wrapper {
		display: grid;
		background-color: blue;
		grid-template-columns: repeat(14, 1fr);
		grid-column-gap: calc(1rem * 2 + 1px);
	}

	.content-article-wrapper section:first-child {
		grid-column: span 5;
		background-color: teal;
		margin-right: -1rem;
	}

	.content-article-wrapper div {
		grid-column: span 9;
		background-color: pink;
	}

	img {
		width: 100%;
		display: block;
	}

	@media only screen and (max-width: 739px) {
		.content-article-wrapper {
			display: block;
			grid-template-columns: repeat(1, 1fr);
		}

		.content-article-wrapper section:first-child {
			grid-column: 1/2;
			margin-right: 0;
		}

		.content-article-wrapper section:last-child {
			grid-column: 1/2;
		}

		img {
			width: 100%;
			display: block;
			margin-bottom: 1.25rem;
		}
	}
</style>
