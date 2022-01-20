<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import MouseBird from "./MouseBird.svelte";
  import Cloud from "./Cloud.svelte";
  import TextOverlay from "./TextOverlay.svelte";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";

  let scrollOverlayVisible = true;
  let clickOverlayVisible = false;

  // init gsap
  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    // Horizontal Scroll
    gsap.to("#landscape", {
      x: -window.innerHeight * (13912 / 1080) + window.innerWidth,
      ease: "none",
      scrollTrigger: {
        trigger: "#landscape",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + landscape.offsetWidth * 2,
        onUpdate: (self) => {
          //console.log("🚀 ~ file: LandscapeScene.svelte ~ line 31 ~ onMount ~ self.progress", self.progress);
          scrollOverlayVisible = (self.progress > 0.01) ? false : true;
          clickOverlayVisible = (self.progress > 0.99) ? true : false;
        },
      },
    });

    // Horizontal Scroll Background
    gsap.to("#background", {
      x: -window.innerHeight * (13912 / 1080) + window.innerWidth,
      ease: "none",
      scrollTrigger: {
        trigger: "#background",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + landscape.offsetWidth * 2,
      },
    });
  });
</script>

<PaperTileBackground widthPx={window.innerWidth * 10} heightPx={window.innerHeight} />

<div id="landscape">
  <img id="landscape-image" src="/images/landscape.png" alt="Landscape Illustration" />
  <!-- <Cloud variant=0 parallaxSpeed=10/> -->
</div>

{#if scrollOverlayVisible}
  <TextOverlay text="Scroll down <br> v" />
{/if}

{#if clickOverlayVisible}
  <TextOverlay text="Click to continue" />
{/if}

<MouseBird/>


<style>
  #landscape {
    /* background-color: rgba(235, 217, 135, 0.39); */
    position: relative;
    height: 100vh;
    width: fit-content;
    /* overflow: hidden; */

    

    display: flex;
    align-items: flex-start;

    mix-blend-mode: multiply;
    /* display: none; */
  }

  img {
    height: 100%;
    width: auto;
    /* position: absolute;
    height: 150vh;
    top: -50vh; */
  }
</style>
