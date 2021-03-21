<script>
  export let jobs;
  export let active;
  export let bars;

  $: macros = generateMacros(active);

  function generateLines() {
    const lines = [];
    jobs.forEach((job, index) => {
      if (active != index) {
        for (let i = 0; i < bars; i++) {
          lines.push(`/hotbar copy ${jobs[active]} ${i + 1} ${job} ${i + 1}`);
        }
      }
    });
    return lines;
  }

  function generateMacros(from) {
    const macros = [];
    const lines = generateLines();
    const macrosNeeded = Math.ceil(lines.length / 15);
    for (let i = 0; i < macrosNeeded; i++) {
      macros.push(lines.slice(i * 15, i * 15 + 15));
    }
    return macros;
  }
</script>

<style>
  h3 {
    font-weight: 400;
    font-style: italic;
    font-size: 2rem;
    margin: 0 20px 0 20px;
    text-align: right;
  }
  .macros {
    display: flex;
    flex-wrap: wrap;
    justify-content: right;
    padding: 5px;
    font-size: 2rem;
  }
  .macros > div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: top;
    min-width: 230px;
    margin: 5px;
    background: #4c2418;
    font-size: 1.2rem;
    padding: 0.5rem 1rem;
    text-align: left;
  }
  button {
    background: #1e1411;
    color: #c5954f;
    font-family: "Alegreya", serif;
    text-transform: uppercase;
    font-size: 1.2rem;
    width: 5rem;
    border: none;
  }
</style>

<div>
  <h3>with these ingame macros.</h3>
  <div class="macros">
    {#each macros as macro}
      <div>
      <button>copy</button>
        {#each macro as line}
          {line} <br>
        {/each}
      </div>
    {/each}
  </div>
</div>