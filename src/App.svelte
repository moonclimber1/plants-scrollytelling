<script>
	import SceneMouseFollow from "./SceneMouseFollow.svelte";
	import PathAnimation from "./PathAnimation.svelte";
	import Scene1 from "./Scene1.svelte";
</script>

<main>
	<!-- <SceneMouseFollow/> -->
	<!-- <PathAnimation/> -->
	<Scene1/>
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