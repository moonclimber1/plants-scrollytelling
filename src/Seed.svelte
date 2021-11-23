<script>
    import { gsap } from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { MotionPathPlugin } from "gsap/MotionPathPlugin";
    gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);
    
    const tl = gsap.timeline();

    import { spring } from 'svelte/motion';

    let coords = spring({ x: 500, y: 500 }, {
		stiffness: 0.05,
		damping: 0.9
	});

    function onMouseMove(event){
        coords.set({ x: event.clientX, y: event.clientY })
    }
</script>


<div on:mousemove="{e => onMouseMove(e)}">
    <img style="transform:translate({$coords.x}px,{$coords.y}px)" src="./images/seed.png" alt="Seed">
</div>


<style>
    div{
        width: 100%;
        height: 100%;
        position: fixed;
    }

    img{
        height: 60px;
        width: auto;

        position: absolute;
        top: -30px;
        left: -15px;
    }

</style>