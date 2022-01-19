<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import BirdScene from "./BirdScene.svelte";
  import TextOverlay from "./TextOverlay.svelte";
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import SeedPathAnimation from "./SeedPathAnimation.svelte";

  let overlayVisible = true;
  let birdSceneVisible = false;
  let seedAnimationState = 0; 

  // init gsap
  gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
  gsap.registerPlugin(CustomEase);

  onMount(() => {
    // Horizontal Scroll Foreground
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
          overlayVisible = (self.progress > 0.03) ? false : true;
          birdSceneVisible = (self.progress == 1) ? true : false;
        
          if (self.progress < 0.33) {
            seedAnimationState = Math.floor(self.progress * 3 * 6.99);
          }
        },
      },
    });

    // Horizontal Scroll Background
    gsap.to("#background", {
      x: -window.innerWidth * 1.4,
      ease: "none",
      scrollTrigger: {
        trigger: "#background",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 3,
      },
    });
  });
</script>

<PaperTileBackground widthPx={window.innerWidth * 3} />

<div id="container">
  <img id="window" src="/images/window-new.png" alt="Window" />
  <SeedPathAnimation seedAnimationState={seedAnimationState}/>
</div>

{#if overlayVisible}
  <TextOverlay text="Scroll down <br> v" />
{/if}

{#if birdSceneVisible}
  <BirdScene/>
{/if}

<div id="trigger" />

<style>
  #container {
    /* background-color: rgba(235, 217, 135, 0.39); */

    height: 100vh;
    width: 600vw;
    /* width: fit-content; */
    /* overflow: hidden; */

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
