<main>
	<!--[if lt IE 7]>
			<p class="browsehappy">You are using an <strong>outdated</strong> browser. Please <a href="#">upgrade your browser</a> to improve your experience.</p>
		<![endif]-->
	<div>
		<div>
		<slot />
		</div>
	</div>
</main>

<style>
	div {
		max-width: 1200px;
		padding: 0 3%;
		background-color: blue;
	}

	div > div {
		background-color: red;
		display: flex;
		flex-direction: column;
	}

</style>