<script>
	export let articles = [];
</script>

{#if articles}
	<div class="content-article-wrapper">
		<section class="first">
			<h3>{articles[0].title}</h3>
			<p>{articles[0].abstract}</p>
		</section>
		<section class="second">
			<h3>{articles[1].title}</h3>
			<p>{articles[1].abstract}</p>
		</section>
		<div class="image">
			<img src={articles[0].multimedia[1].url} />
		</div>
	</div>
{/if}

<style>
	.content-article-wrapper {
		display: grid;
		grid-column-gap: calc(1rem * 2 + 1px);
		grid-template-areas:
			'first image'
			'second image';
		grid-template-columns: repeat(14, 1fr);
	}

	.content-article-wrapper .first {
		grid-area: first;
		grid-column: 1/6;
		margin-right: -1rem;
	}

	.content-article-wrapper .first::after {
		content: '';
		display: block;
		margin-top: 1rem;
		margin-bottom: 1rem;	
		border-bottom: 1px solid var(--color-stroke-quaternary);
	}

	.content-article-wrapper .second {
		grid-area: second;
		grid-column: 1/6;
		margin-right: -1rem;
	}

	.content-article-wrapper .image {
		grid-area: image;
		grid-column: 6/15;
	}

	img {
		display: block;
		width: 100%;
		margin-bottom: 1.25rem;
	}

	h3 {
		margin: 0px
	}

	@media only screen and (max-width: 739px) {
		.content-article-wrapper {
			grid-template-areas:
				'first'
				'image'
				'second';
		}

		.content-article-wrapper .first {
			grid-column: 1/15;
			margin-right: 0;
		}

		.content-article-wrapper .first::after {
			content: none;
		}

		.content-article-wrapper .second {
			grid-column: 1/15;
		}

		.content-article-wrapper .image {
			grid-column: 1/15;
		}

	}
</style>
