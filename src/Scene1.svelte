<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import ImageBackground from "./ImageBackground.svelte";
  import BasicSeed from "./BasicSeed.svelte";
  import TextOverlay from "./TextOverlay.svelte";
  import PaperTileBackground from "./PaperTileBackground.svelte";

  let overlayVisible = true;

  // init gsap
  gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
  gsap.registerPlugin(CustomEase);

  onMount(() => {
    // const tl = gsap.timeline({
    //   scrollTrigger: {
    //     trigger: "#container",
    //     pin: true,
    //     scrub: 1,
    //     snap: false,
    //     end: () => "+=" + window.innerWidth * 2,
    //     onUpdate: (self) => {
    //       if (self.progress > 0.02) {
    //         overlayVisible = false;
    //       }
    //     },
    //   },
    // });

    // tl.to("#container", {
    //   x: -window.innerWidth * 3,
    //   ease: "none",
    // });
    // tl.to("#background", {
    //   x: -window.innerWidth * 3,
    //   ease: "none",
    // });

    const endPixel = 5000;
    // // Horizontal Scroll
    gsap.to("#container", {
      // xPercent: -100,
      x: -window.innerWidth * 1.4,
      ease: "none",
      scrollTrigger: {
        trigger: "#container",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 3,
        onUpdate: (self) => {
          if (self.progress > 0.02) {
            console.log("🚀 ~ file: Scene1.svelte ~ line 58 ~ onMount ~ self.progress", self.progress)
            overlayVisible = false;
            
          }
        },
      },
    });

    gsap.to("#background", {
      x: -window.innerWidth*1.4,
      ease: "none",
      scrollTrigger: {
        trigger: "#background",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" +  window.innerWidth * 3,
      },
    });
  });
</script>

<PaperTileBackground widthPx={window.innerWidth * 3000} />
<!-- <ImageBackground imagePath="/images/paper-background-1.jpeg" /> -->
<div id="container">
  <img id="window" src="/images/window-new.png" alt="Window" />
  <BasicSeed />
</div>

{#if overlayVisible}
  <TextOverlay text="Scroll down <br> v" />
{/if}

<div id="trigger" />

<style>
  #container {
    /* background-color: rgba(235, 217, 135, 0.39); */

    height: 100vh;
    width: 6000vw;
    /* width: fit-content; */
    overflow: hidden;

    position: relative;

    display: flex;
    align-items: flex-start;

    mix-blend-mode: multiply;
  }

  img {
    position: relative;
    top: -60vh;

    width: 150vw;
  }

  #trigger {
    width: 20px;
    height: 20px;
    background-color: green;
    position: absolute;
    top: 120vh;
  }
</style>
