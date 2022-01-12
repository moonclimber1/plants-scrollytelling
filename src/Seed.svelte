<script>
    // Imports
    import { spring } from 'svelte/motion';
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";

    // init gsap
    gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
    const tl = gsap.timeline();

    // set up seed easying
    let coords = spring({ x: window.innerWidth/2, y: window.innerHeight/3 }, {
		stiffness: 0.05,
		damping: 0.9
	});

    function onMouseMove(event){
        coords.set({ x: event.clientX, y: event.clientY })
    }

    var seedImages = ["./images/Lavendel_sad.png", "./images/Lavendel_sad_very.png"]
    var currentImageIndex = 0

    function onSeedClick(){
        console.log("seed clicked", tl)
        currentImageIndex = (currentImageIndex+1) % seedImages.length;
    }
</script>


<div on:mousemove="{e => onMouseMove(e)}">
    <img on:click={onSeedClick} style="transform:translate({$coords.x}px,{$coords.y}px)" src="{seedImages[currentImageIndex]}" alt="Seed">
</div>


<style>
    div{
        width: 100%;
        height: 100%;
        position: fixed;

        mix-blend-mode:multiply;
    }

    img{
        height: 100px;
        width: auto;

        position: absolute;
        top: -50px;
        left: -35px;
    }

</style>