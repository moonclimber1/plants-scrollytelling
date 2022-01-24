<script>
  export let variant = 3 

  const cloudImages = ["./images/clouds/cloud-1.png", "./images/clouds/cloud-1.png"];

</script>

<img id="cloud-img" src="{"./images/clouds/cloud-" + variant + ".png"}" alt="Cloud" />

<style>
    #cloud-img{
        width: 12vw;
        height: 8vw;

        position: absolute;
        top: 0;
        left: 0;
    }
</style>
