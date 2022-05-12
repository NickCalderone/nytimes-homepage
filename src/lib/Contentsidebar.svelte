<div class="content">
	<div>my left section</div>
	<div>my right section</div>
</div>

<style>
	.content {
		display: grid;
		grid-column-gap: calc(1rem * 2 + 1px);
		grid-template-columns: repeat(20, 1fr);
	}

	.content div:first-child {
		grid-area: left;
		grid-column: span 14;
		background-color: orange;
	}

	.content div:last-child {
		grid-area: right;
		grid-column: span 6;
		background-color: grey;
		position: relative;
	}

	.content div:last-child::before {
		content: '';
		height: 100%;
		position: absolute;
		left: calc(-1rem - 1px);
		border-left: grey 1px solid;
	}

</style>