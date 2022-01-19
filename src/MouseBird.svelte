<script>
    // Imports
    import { spring } from 'svelte/motion';
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";

    // set up seed easying
    let coords = spring({ x: window.innerWidth/4, y: window.innerHeight/3 }, {
		stiffness: 0.03,
		damping: 0.9
	});

    function onMouseMove(event){
        // coords.set({ x: event.clientX, y: event.clientY })
        console.log("🚀 ~ file: MouseBird.svelte ~ line 16 ~ onMouseMove ~ event.clientY", event.clientY)
        console.log("🚀 ~ file: MouseBird.svelte ~ line 16 ~ onMouseMove ~ event.clientX", event.clientX)
        coords.set({ x: $coords.x, y: event.clientY })
    }

    var birdImages = ["./images/Bird_full.png"]
    var currentImageIndex = 0

    function onBirdClick(){
        console.log("seed clicked", tl)
        currentImageIndex = (currentImageIndex+1) % birdImages.length;
    }
</script>


<div on:mousemove="{e => onMouseMove(e)}">
    <img on:click={onBirdClick} style="transform:translate({$coords.x}px,{$coords.y}px)" src="{birdImages[currentImageIndex]}" alt="Flying Bird">
</div>


<style>
    div{
        position: fixed;
        width: 100vw;
        height: 100vh;
        top: 0;
        

        /* mix-blend-mode:multiply; */

        /* z-index: 100; */
        /* background-color: tomato; */
    }

    img{
        height: 100px;
        width: auto;

        position: absolute;
        top: -50px;
        left: -35px;
    }


    h2 {
    position: fixed;
    top: 82vh;
    width: 100vw;

    margin: 0;

    font-size: xx-large;
    font-style: normal;
    line-height: 1.5rem;

    pointer-events: none;
  }

</style>