<script>
  export let animationState = 0;
  const seedImages = [
    "./images/lavendel-emotions/Lavendel_sad.png",
    "./images/lavendel-emotions/Lavendel_sad_very.png",
    "./images/lavendel-emotions/Lavendel_sad_very_02.png",
    "./images/lavendel-emotions/Tear_02.png",
    "./images/lavendel-emotions/Tear_03.png",
    "./images/lavendel-emotions/Tear_04.png",
    "./images/lavendel-emotions/Tear_05.png",
  ];

  // Imports
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  // init gsap
  gsap.registerPlugin(ScrollTrigger);
  
  onMount(() => {
    console.log("i got mounted")
    gsap.from("#seed-wrapper", {
      yPercent: -100,
      xPercent: -30,
      scrollTrigger: {
        trigger: "#seed-wrapper",
        pin: false,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * 3,
      },
    })
  });
  
</script>

<div id="seed-wrapper">
  <img id="seed-img" src={seedImages[animationState]} alt="Seed" />
</div>

<style>
  #seed-wrapper {
    height: 100px;
    width: auto;
    position: absolute;
    top: 70vh;
    left: 40vw;
  }

  img {
    height: 100%;

    position: relative;
    top: -50px;
    left: -35px;
  }
</style>
