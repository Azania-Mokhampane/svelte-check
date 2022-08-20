<script>
  import { onMount } from "svelte";
  import axios from "axios";

  let data;

  onMount(async () => {
    await axios
      .get("https://swapi.dev/api/people")
      .then((res) => (data = res.data.results));
  });
</script>

<p>Stars Wars API</p>

{#if !data}
  <p>Fetching Data...</p>
{:else}
  {#each data as person}
    <h3>{person.name}</h3>
    <p>{person.skin_color}</p>
  {/each}
{/if}

<style>
  button {
    font-family: inherit;
    font-size: inherit;
    padding: 1em 2em;
    color: #ff3e00;
    background-color: rgba(255, 62, 0, 0.1);
    border-radius: 2em;
    border: 2px solid rgba(255, 62, 0, 0);
    outline: none;
    width: 200px;
    font-variant-numeric: tabular-nums;
    cursor: pointer;
  }

  button:focus {
    border: 2px solid #ff3e00;
  }

  button:active {
    background-color: rgba(255, 62, 0, 0.2);
  }
  h3 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 25px;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }
  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }
</style>
