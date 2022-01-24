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
        let x = event.clientX // $coords.x
        let y = event.clientY
        coords.set({ x: x, y: y })
    }

    var birdImages = ["./images/Bird_full.png"]
    var currentImageIndex = 0

    function onBirdClick(){
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

        z-index: 100;
        /* background-color: tomato; */
        
    }

    img{
        height: 100px;
        width: auto;

        position: absolute;
        top: -20px;
        left: -120px;
    }

</style>