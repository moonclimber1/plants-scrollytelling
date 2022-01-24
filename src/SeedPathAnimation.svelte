<script>
  export let seedAnimationState = 0;

  // Imports
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { MotionPathPlugin } from "gsap/MotionPathPlugin";
  import { CustomEase } from "gsap/CustomEase";
  import { onMount } from "svelte";
  import Seed from "./Seed.svelte";

  // init gsap
  gsap.registerPlugin(ScrollTrigger, MotionPathPlugin, CustomEase);

  onMount(() => {
    gsap.to("#seed-wrapper", {
      motionPath: { path: "#lavendel-jump-path", align: "#lavendel-jump-path" },
      scrollTrigger: {
        trigger: "#seed-img",
        start: () => "top top+=" + 1,
        pin: false,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 3,
      },
    });
  });
</script>

<Seed animationState={seedAnimationState}/>

<svg width="95vw" viewBox="0 0 5331 1908" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path
    id="lavendel-jump-path"
    d="M1 0.5C101.5 744.667 375.2 2119.1 646 1877.5C984.5 1575.5 1273 298 1483 572.5C1693 847 1798.5 1840 2183 1904C2567.5 1968 2706.5 962 3072.5 998.5C3365.3 1027.7 3693.5 1704 5330 1761.5"
    stroke="black"
  />
</svg>

<style>
  #seed-wrapper {
    height: 100px;
    width: auto;
  }

  img {
    height: 100%;

    position: relative;
    top: -50px;
    left: -35px;
  }

  /* #box {
    width: 20px;
    height: 20px;

    background-color: blueviolet;

    position: absolute;
  } */

  svg {
    /* background-color: green; */

    position: absolute;
    top: 20vh;
    left: 30vw;

    opacity: 0;
  }
</style>
