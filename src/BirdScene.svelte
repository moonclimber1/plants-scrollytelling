<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import Seed from "./Seed.svelte";
  import TextOverlay from "./TextOverlay.svelte";
  import BigBird from "./BigBird.svelte";
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import { activeComponentIndex } from "./stores.js";

  let overlayVisible = false;

  // init gsap
  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    gsap.from("#seed-container", {
      x: -window.innerWidth / 2,
      ease: "none",
      scrollTrigger: {
        trigger: "#bird-scene-container",
        pin: false,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 1.5,
      },
    });
    gsap.from("#bird-container", {
      y: window.innerHeight / 2,
      ease: "none",
      scrollTrigger: {
        trigger: "#trigger",
        pin: false,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth / 2,
        onUpdate: (self) => {
          overlayVisible = self.progress > 0.8 ? true : false;
        },
      },
    });
  });
</script>

<div id="bird-scene-container">
  <div id="seed-container">
    <Seed animationState="6" />
  </div>
  <div id="bird-container">
    <BigBird animationState="1" />
  </div>
</div>
{#if overlayVisible}
  <TextOverlay text="Click to continue" />
{/if}
<svelte:window
  on:click={() => {
    // gsap.killTweensOf("*");
    activeComponentIndex.update((n) => 1);
  }}
/>

<style>
  #bird-scene-container {
    /* background-color: rgba(255, 99, 71, 0.1); */
    height: 100vh;
    width: 100vw;
    overflow: hidden;

    position: fixed;
    top: 0;
    left: 0;
  }

  #seed-container {
    position: absolute;
    top: 70vh;
    left: 35vw;
    width: fit-content;
    height: fit-content;
  }

  #bird-container {
    position: absolute;
    bottom: -20vh;
    left: 27vw;
    transform: rotateZ(-100deg);
  }
</style>
