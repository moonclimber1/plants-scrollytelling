<script>
    export let animationState = 0;
    var seedImages = ["./images/Lavendel_sad.png", "./images/Lavendel_sad_very.png"]
</script>

<img src="{seedImages[animationState]}" alt="Seed">

<style>
    img{
        height: 100px;
        width: auto;

        position: relative;
        top: -50px;
        left: -35px;
    }
</style>