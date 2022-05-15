<script>
	export let articles;
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
	<div class="content-article-bottom-wrapper">
		<section>
			<h3>{articles[2].title}</h3>
		</section>
		<section>
			<h3>{articles[3].title}</h3>
		</section>
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

	.content-article-wrapper::after {
		content: '';
		display: block;
		margin-top: 1rem;
		margin-bottom: 1rem;
		border-bottom: 1px solid var(--color-stroke-quaternary);
		grid-column: 1/-1;
		clear: both;
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
	}

	h3 {
		margin: 0px;
	}

	.content-article-bottom-wrapper {
		display: grid;
		grid-template-columns: repeat(14, 1fr);
		grid-gap: calc(1rem * 2 + 1px);
		background-color: green;
	}

	.content-article-bottom-wrapper section:first-child {
		grid-column: 1/8;
	}

	.content-article-bottom-wrapper section:nth-child(2) {
		grid-column: 8/15;
		position: relative;
	}

	.content-article-bottom-wrapper section:nth-child(2)::before {
		content: '';
		position: absolute;
		height: 100%;
		left: calc(-1rem - 1px);
		border-left: 1px solid var(--color-stroke-quaternary);
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
			margin-bottom: 1.25rem;
		}

		.content-article-bottom-wrapper {
			display: block;
		}

		.content-article-bottom-wrapper section:nth-child(1)::after {
			content: '';
			display: block;
			margin-top: 1rem;
			margin-bottom: 1rem;
			border-bottom: 1px solid var(--color-stroke-quaternary);
		}

		.content-article-bottom-wrapper section:nth-child(2)::before {
			content: none;
		}
	}
</style>
