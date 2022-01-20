<script>
  import Seed from "./Seed.svelte";
</script>

<div id="end-container">
  <img id="end-image" src="/images/landscape.png" alt="End Scene" />
</div>
<Seed />

<style>
  #end-container {
    position: relative;
    height: 100vh;
    width: 100vw;
    overflow: hidden;

    display: flex;
    align-items: flex-start;
    justify-content: flex-end;

    mix-blend-mode: multiply;
  }

  #end-image {
    /* height: 100%;
    width: auto; */

    position: relative;
    top: -140vh; 

    right: -55vw;

    height: 250vh;
    width: auto;
  }

</style>
