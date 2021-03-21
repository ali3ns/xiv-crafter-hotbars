<script>
   import Picker from "./Picker.svelte";
   import Macro from "./Macro.svelte";

   const jobs = ["alc", "arm", "bsm", "crp", "cul", "gsm", "ltw", "wvr"];
   let from = 0;
   let bars = 5;
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Alegreya:ital@0;1&display=swap");
  :global(body) {
    background: #14140e;
    color: #c5954f;
  }
  main {
    font-family: "Alegreya", serif;
    text-align: center;
  }
  h1 {
    font-weight: 400;
    text-transform: uppercase;
    font-size: 5rem;
    line-height: 4.5rem;
  }
</style>

<main>
	<h1>Crafter hotbars</h1>
  <Picker jobs={jobs} bind:active={from} bind:bars={bars} />
  <Macro jobs={jobs} active={from} bars={bars} />
</main>