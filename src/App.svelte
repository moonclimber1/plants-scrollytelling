<script>
	import Seed from "./Seed.svelte";
	export let name;
</script>

<main>
	<h1>Hello {name} Plants!</h1>
	<Seed/>
</main>

<style>
	main {
		text-align: center;
		padding: 0;
		max-width: 240px;
		margin: 0;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		background-color: aliceblue;
		width: 100vw;
		position: fixed;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>