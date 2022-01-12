<script>
    // Imports
    import { spring } from 'svelte/motion';
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";

    // init gsap
    gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
    const tl = gsap.timeline();

</script>

<div>

</div>

<style>
    div{
        width: 100px;
        height: 100px;
        background-color: aqua;
    }
</style>