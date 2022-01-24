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
    "./images/lavendel-emotions/Lavendel_happy_02.png"
  ];
  
</script>

<div id="seed-wrapper">
  <img id="seed-img" src={seedImages[animationState]} alt="Seed" />
</div>

<style>
  #seed-wrapper {
    height: 100px;
    width: auto;
    position: absolute;
    top: 0;
    left: 0;
    /* background-color: chartreuse; */
  }

  img {
    height: 100%;

    position: relative;
    top: -50px;
    left: -35px;
  }
</style>
