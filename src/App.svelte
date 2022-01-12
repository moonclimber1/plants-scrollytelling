<script>
	import SceneMouseFollow from "./SceneMouseFollow.svelte";
	import PathAnimation from "./PathAnimation.svelte";
</script>

<main>
	<!-- <SceneMouseFollow/> -->
	<PathAnimation/>
</main>

<style>
	main {
		text-align: center;
		padding: 0;
		max-width: 240px;
		margin: 0;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>