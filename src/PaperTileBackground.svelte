
<script>
	 export let widthPx = "15000";
	 export let heightPx = "15000";

	 export let locomotiveMode = false;

	//  const roughness = 2;
	//  $: sizePx = widthPx/roughness;

	const sizePx = 600;
	 
</script>

<div id="background" class:default-mode={!locomotiveMode} style="--width:{widthPx + "px"}; --height:{heightPx + "px"}; --size:{sizePx + "px"}"></div>

<style>
	#background{
		width: var(--width);
		height: var(--height);
		
		background-image: url("/images/paper-tile-5.jpeg");
		background-repeat: repeat;
		background-size: var(--size);

		opacity: 0.8;
		/* background-size: cover; */
	}
	.default-mode{
		position: absolute;
		top: 0;
	}
</style>