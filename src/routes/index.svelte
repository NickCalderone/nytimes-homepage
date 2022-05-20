<script>
	import Contentsidebar from '../lib/Contentsidebar.svelte';

	function buildSectionsArray(data, randomNumber, layoutArray) {
		console.log(layoutArray);
		let dataLength = data.length;
		let furthestIndex = layoutArray[layoutArray.length - 1][1];
		console.log('furthestIndex ', furthestIndex);

		let myNumber = randomNumber();
		console.log('muynumber is ', myNumber);

		if (furthestIndex + myNumber > dataLength + 1) {
			console.log('went over, tring again');
			return buildSectionsArray(data, randomNumber, layoutArray);
		} else if (furthestIndex + myNumber < dataLength + 1) {
			return buildSectionsArray(data, randomNumber, [
				...layoutArray,
				[furthestIndex, furthestIndex + myNumber]
			]);
		} else if (furthestIndex + myNumber === dataLength + 1) {
			return [...layoutArray, [furthestIndex, furthestIndex + myNumber]];
		} else {
			console.log('Made it throughbuildSectionsArray without finishing');
		}
	}

	function generateNumber() {
		return Math.floor(Math.random() * 4 + 1);
	}

	async function getHomepageArticles() {
		const response = await fetch(
			'https://api.nytimes.com/svc/topstories/v2/home.json?api-key=GxINPsIPrAO6UJucICIvNPAzrgb2ourt'
		);
		const data = await response.json();

		if (response.ok) {
			console.log('data', data.results);
			return data.results;
		} else {
			throw new Error(data);
		}
	}

	async function makeLayout() {
		let x = await getHomepageArticles();

		let y = buildSectionsArray(x, generateNumber, [[0, generateNumber()]]);
		return [x, y];
	}
	let answer = makeLayout();
</script>

{#await answer}
	<p>Loading</p>
{:then myAnswer}
	<Contentsidebar articles={myAnswer[0]} layout={myAnswer[1]} />
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<style>
	main {
		height: 100%;
	}
</style>
