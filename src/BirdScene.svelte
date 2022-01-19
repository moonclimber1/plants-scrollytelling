<script>
    // Imports
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";
    import { CustomEase } from "gsap/CustomEase";
    import { onMount } from "svelte";
    import Seed from "./Seed.svelte";
    import TextOverlay from "./TextOverlay.svelte";
    import PaperTileBackground from "./PaperTileBackground.svelte";

</script>

<div id="bird-scene-container">
    <Seed/>
</div>


<style>

#bird-scene-container{
    background-color: rgba(255, 99, 71, 0.1);
    height: 100vh;
    width: 100vw;
    overflow: hidden;

    position: fixed;
    top: 0;
    left: 0;
  }

</style>