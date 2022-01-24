<script>
  export let animationState = 1;
  const birdImages = ["./images/Magpie_closed.png", "./images/Magpie_open.png"];
</script>

<img id="bird-img" src={birdImages[animationState]} alt="Bird" />

<style>
  #bird-img {
    height: 300px;
    width: auto;
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
