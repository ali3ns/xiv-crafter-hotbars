<script>
  export let jobs;
  export let active;
  export let bars;

  function setActive(i) {
    active = i;
  }
</script>

<style>
  h3 {
    font-weight: 400;
    font-style: italic;
    font-size: 2rem;
    margin: 0 0 0 20px;
    text-align: left;
  }

  h3 span {
    color: #8a0f0a;
    font-weight: 900;
    text-transform: uppercase;
    font-size: 2.6rem;
    padding: 0 0.2rem;
  }
  .flex {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    padding: 5px;
    text-transform: uppercase;
    font-size: 2rem;
  }
  .flex > div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 120px;
    height: 120px;
    margin: 5px;
    background: #4c2418;
    cursor: pointer;
  }
  .flex > div.active {
    background: #8a0f0a;
    color: #14140e;
  }
</style>

<div>
  <h3>Copy the first <span>{bars}</span> {bars > 1 ? 'hotbars' : 'hotbar'} from <span>{jobs[active]}</span> to all other crafters</h3>
  <div class="flex">
    {#each jobs as job, i}
      <div class:active="{active === i}" on:click={() => setActive(i)}>
      { job }
      </div>
    {/each}
  </div>
</div>