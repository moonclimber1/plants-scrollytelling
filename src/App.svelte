<script>
  import SceneMouseFollow from "./SceneMouseFollow.svelte";
  import PathAnimation from "./PathAnimation.svelte";
  import Scene1 from "./Scene1.svelte";
  import LandscapeScene from "./LandscapeScene.svelte";
  import LandscapeScene2 from "./LandscapeScene2.svelte";
  import EndScene from "./EndScene.svelte";
  import { activeComponentIndex } from "./stores.js";

  let activeComponent = 0;

  activeComponentIndex.subscribe((val) => {
    activeComponent = val;
  });

  $: console.log("active component", activeComponent);
</script>

<main>
  {#if activeComponent == 0}
    <Scene1 />
  {:else if activeComponent == 1}
    <LandscapeScene />
  {:else if activeComponent == 2}
    <EndScene/>
  {/if}

  <!-- <SceneMouseFollow/> -->
  <!-- <PathAnimation/> -->

  <!-- <LandscapeScene2/> -->
  <!-- <EndScene/> -->
</main>

<style>
  main {
    text-align: center;
    padding: 0;
    max-width: 240px;
    margin: 0;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
