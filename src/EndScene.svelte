<script>
  import Seed from "./Seed.svelte";
  import PaperTileBackground from "./PaperTileBackground.svelte";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { onMount } from "svelte";

  // init gsap
  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    const tl = gsap.timeline();
    tl.from("#seed-container", {
      y: -window.innerHeight,
      duration: 3,
    });
    tl.from(["#sweet", "#main", "#moustache"], {
      scale: 0,
      duration: 2,
      stagger: 0.5,
      transformOrigin: "center bottom"
    } )
  });
</script>

<PaperTileBackground widthPx={window.innerWidth} heightPx={window.innerHeight} />

<div id="end-container">
  <img id="end-image" src="/images/landscape.png" alt="End Scene" />
</div>

<div id="seed-container">
  <Seed animationState="7" />
</div>

<img id="main" src="/images/friends/main-norm.png" alt="">
<img id="moustache" src="/images/friends/moustache-norm.png" alt="">
<img id="sweet" src="/images/friends/sweet-norm.png" alt="">

<style>

  #main{
    position: absolute;
    bottom: 12vh;
    right: 27vw;
    height: 250px;
    width: auto;
  }

  #moustache{
    position: absolute;
    bottom: 10vh;
    right: 23vw;
    height: 270px;
    width: auto;
  }

  #sweet{
    position: absolute;
    bottom: 12vh;
    right: 35vw;
    height: 240px;
    width: auto;
  }
  #end-container {
    position: relative;
    height: 100vh;
    width: 100vw;
    overflow: hidden;

    display: flex;
    align-items: flex-start;
    justify-content: flex-end;

    mix-blend-mode: multiply;
  }

  #end-image {
    /* height: 100%;
    width: auto; */

    position: relative;
    top: -140vh;

    right: -55vw;

    height: 250vh;
    width: auto;
  }

  #seed-container {
    position: absolute;
    top: 80vh;
    left: 60vw;
    width: fit-content;
    height: fit-content;
  }
</style>
