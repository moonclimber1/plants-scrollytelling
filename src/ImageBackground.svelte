
<script>
	 export let imagePath;
</script>

<div id="background" style="--image-path: url({imagePath})"></div>

<style>
	#background{
		width: 100%;
		height: 100%;
		position: fixed;

		background-image: var(--image-path);
		background-size: cover;
	}
</style>