
<script>
	 export let imagePath;
</script>

<div id="background" style="--image-path: url({imagePath})"></div>

<style>
	#background{
		width: 3000vw;
		height: 3000vh;
		position: absolute;
		top: 0;

		background-image: url("/images/paper-background-1.jpeg");
		background-repeat: repeat;
		background-size: 2%;
		/* background-size: cover; */
	}
</style>