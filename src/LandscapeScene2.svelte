<script>
  // Imports
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import MouseBird from "./MouseBird.svelte";
  import Cloud2 from "./Cloud2.svelte";
  import TextOverlay from "./TextOverlay.svelte";
  import { onMount } from "svelte";
  import LocomotiveScroll from "locomotive-scroll";

  let scrollOverlayVisible = true;
  let clickOverlayVisible = false;

  // const scroll = null;

  onMount(() => {
    const scroll = new LocomotiveScroll({
      el: document.querySelector("[data-scroll-container]"),
      smooth: true,
      direction: "horizontal",
    });
    // console.log("🚀 ~ file: LandscapeScene2.svelte ~ line 18 ~ onMount ~ scroll", scroll);
  });
</script>

<MouseBird/>
<div data-scroll-container>
  <PaperTileBackground locomotiveMode="true" widthPx={window.innerHeight * (13912 / 1080)} heightPx={window.innerHeight} />
  <img data-scroll data-scroll-speed="0" id="landscape-image" src="/images/landscape.png" alt="Landscape Illustration" />
  <div id="cloud-container" data-scroll data-scroll-speed="4"style="position: absolute; top: 20vh; left: 100vw">
    <Cloud2/>
  </div>
</div>


<!-- {#if scrollOverlayVisible}
  <TextOverlay text="Scroll down <br> v" />
{/if}

{#if clickOverlayVisible}
  <TextOverlay text="Click to continue" />
{/if} -->


<style>
  #landscape-image {
    height: 100vh;
    width: auto;
    position: absolute;
    top: 0;
    left: 0px;

    pointer-events: none;
  }

  #cloud-container {
    width: fit-content;
    height: fit-content;
    mix-blend-mode: multiply;

    pointer-events: none;
  }
</style>
