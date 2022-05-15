<script>
	import '../app.css';
</script>

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
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 0px auto;
	}
	main > div {
		max-width: 1200px;
		padding: 0 3%;
		background-color: blue;
	}

	main > div > div {
		background-color: red;
		display: flex;
		flex-direction: column;
	}

	@media only screen and (max-width: 739px){
		main > div {
			padding: 0 1.25rem;
		}
	}

</style>