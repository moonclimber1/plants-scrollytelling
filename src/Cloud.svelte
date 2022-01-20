<script>
  export let animationState = 0;

  export let variant = 0 
  export let parallaxSpeed = 100;

  const cloudImages = ["./images/lavendel-emotions/Lavendel_sad.png"];

  // Imports
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  // init gsap
  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    // gsap.from("#seed-wrapper", {
    //   yPercent: -100,
    //   xPercent: -30,
    //   scrollTrigger: {
    //     trigger: "#seed-wrapper",
    //     pin: false,
    //     scrub: 1,
    //     snap: false,
    //     end: () => "+=" + window.innerWidth * 3,
    //   },
    // });

    gsap.to("#cloud-img", {
      x: -window.innerHeight * (13912 / 1080) + window.innerWidth,
      ease: "none",
      scrollTrigger: {
        trigger: "#landscape",
        pin: true,
        scrub: 1,
        snap: false,
        end: () => "+=" + window.innerWidth * (100/parallaxSpeed),
      },
    });

  });
</script>

<img id="cloud-img" src="" alt="Cloud" />

<style>
    #cloud-img{
        width: 12vw;
        height: 8vw;
        background-color: tomato;

        position: absolute;
        top: 30vh;
        left: 0vw;
        /* top:0;
        left: 0; */

        mix-blend-mode: multiply;
    }
</style>
