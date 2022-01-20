<script>
  // Imports
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import MouseBird from "./MouseBird.svelte";
  import Cloud from "./Cloud.svelte";
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
    console.log("🚀 ~ file: LandscapeScene2.svelte ~ line 18 ~ onMount ~ scroll", scroll);
  });
</script>

<div data-scroll-container>
  <div data-scroll data-scroll-speed="-1">
    <PaperTileBackground locomotiveMode="true" widthPx={window.innerWidth * 10} heightPx={window.innerHeight * 10} />
    <img id="landscape-image" src="/images/landscape.png" alt="Landscape Illustration" />
  </div>
  <!-- <div data-scroll data-scroll-speed="-1">
      
  </div> -->
</div>

<!-- <div data-scroll-container>
  <div data-scroll-section>
    <h1 data-scroll >Hey</h1>
    <p data-scroll>👋</p>
  </div>
  <div data-scroll-section>
    <h2 data-scroll data-scroll-speed="10">What's up?</h2>
    <p data-scroll data-scroll-speed="2">😬</p>
  </div>
</div> -->

<!-- {#if scrollOverlayVisible}
  <TextOverlay text="Scroll down <br> v" />
{/if}

{#if clickOverlayVisible}
  <TextOverlay text="Click to continue" />
{/if} -->

<!-- <MouseBird /> -->
<style>
  #landscape-image {
    height: 100vh;
    width: auto;
    /* width: calc(100vh * (13912 / 1080)); */
    z-index: 100;
  }
</style>
