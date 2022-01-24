<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import { onDestroy } from 'svelte';
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
      x: -window.innerWidth * 1.35,
      ease: "none",
      scrollTrigger: {
        trigger: "#container",
        id: "t1",
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
      x: -window.innerWidth * 1.35,
      ease: "none",
      scrollTrigger: {
        trigger: "#background",
        id: "t2",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 3,
      },
    });
  });

  onDestroy(() => {
    console.log("Scene 1 got destroyed");
    ScrollTrigger.getById("t1").kill()
    ScrollTrigger.getById("t2").kill()
    // gsap.killTweensOf("#container");
    // gsap.killTweensOf("#background");
	});
</script>

<PaperTileBackground widthPx={window.innerWidth * 3} heightPx={window.innerHeight*9} />

<div id="container">
  <img id="window1" src="/images/window-part-1.png" alt="Window" />
  <img id="window2" src="/images/window-part-2.png" alt="Window" />
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

  #window1 {
    position: relative;
    top: -60vh;

    /* width: 150vw; */
    height: 112vw;
  }

  #window2 {
    position: relative;
    top: -60vh;
    left: -26vw;

    /* width: 150vw; */
    height: 112vw;
    z-index: 10;
  }

  #trigger {
    width: 20px;
    height: 20px;
    background-color: green;
    position: absolute;
    top: 1000vh;
    opacity: 0;
  }
</style>
