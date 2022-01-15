<script>
  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import ImageBackground from "./ImageBackground.svelte";
  import BasicSeed from "./BasicSeed.svelte";

  // init gsap
  gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
  gsap.registerPlugin(CustomEase);
  console.log("🚀 ~ file: Scene1.svelte ~ line 13 ~ CustomEase", CustomEase);

  onMount(() => {
    // Horizontal Scroll
    gsap.to("#container", {
      xPercent: -100,
      ease: "none",
      scrollTrigger: {
        trigger: "#container",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + container.offsetWidth * 2,
      },
    });
    //
    gsap.to("#box", {
      motionPath: { path: "#lavendel-jump-path", align: "#lavendel-jump-path" },
      scrollTrigger: {
        trigger: "#container",
        // start: () => "+=" + -300,
        start: () => "top top+=" + 1, 
        // start: "center left",
        markers: true,
        pin: false,
        scrub: 1,
        snap: false,
        end: () => "+=" + 2000,
      },
    });

    // gsap.to("#box", { duration: 8, delay: 1, motionPath: { path: "#test-path", align: "#test-path" } });
  });
</script>

<ImageBackground imagePath="/images/paper-background-1.jpeg" />
<div id="container">
  <img id="window" src="/images/window-new.png" alt="Window" />
  <!-- <svg width="30vw" viewBox="0 0 3204 1783" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path
      id="test-path"
      d="M5 1083C207.5 634 755.5 -740.5 1339.5 534.5C1517.22 922.492 1641.08 1707.03 2233 1774C2865 1845.5 3925.5 928 2459.5 260.5"
      stroke="black"
      stroke-width="10"
    />
  </svg> -->
  <svg width="60vw" viewBox="0 0 3441 2371" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path
      id="lavendel-jump-path"
      d="M1 0.5C101.5 744.667 370.2 2172.6 641 1931C979.5 1629 1145 266 1355 540.5C1565 815 1574 1867 1958.5 1931C2343 1995 2269.5 961.5 2635.5 998C2928.3 1027.2 3254.5 1955.33 3440.5 2370"
      stroke="black"
    />
  </svg>

  <BasicSeed id="basic-seed"/>

  <div id="box" />
</div>

<style>
  #container {
    /* background-color: skyblue; */

    height: 100vh;
    width: 300vw;
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

  #box {
    width: 20px;
    height: 20px;

    background-color: blueviolet;

    position: absolute;
  }

  svg {
    background-color: green;

    position: absolute;
    top: 20vh;
    left: 70vw;
  }
</style>
