<script>
  export let text = "some text";

  import { fade } from 'svelte/transition';
  import { onMount } from 'svelte';
  import { onDestroy } from 'svelte';

  onMount(() => {
    console.log("TextOverlay got created: ", text);
  })

  onDestroy(() => {
    console.log("TextOverlay got destroyed: ", text);
  })

</script>

<h2 transition:fade="{{duration: 700}}" id="overlay">{@html text}</h2>

<style>
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
