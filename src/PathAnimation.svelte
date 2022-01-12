<script>
    // Imports
    import { spring } from 'svelte/motion';
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";
    import { onMount } from 'svelte';

    // init gsap
    gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
    const tl = gsap.timeline();

    onMount(() => {
        gsap.to("#box", {duration: 8, delay: 1, motionPath: {path: "#test-path", align: "#test-path"}});
    })

</script>

<div>
    <div id="box"></div>
    <svg width="30vw" viewBox="0 0 3204 1783" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path id="test-path" d="M5 1083C207.5 634 755.5 -740.5 1339.5 534.5C1517.22 922.492 1641.08 1707.03 2233 1774C2865 1845.5 3925.5 928 2459.5 260.5" stroke="black" stroke-width="10"/>
    </svg>
</div>

<style>
    div{
        width: 100%;
        height: 100%;
        position: fixed;
        
        background-color: aqua;
    }

   #box{
       width: 20px;
       height: 20px;

       background-color: blueviolet;
   }

    svg{
        background-color: green;
    }
</style>