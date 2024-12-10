<script lang="ts">
  import { onMount } from 'svelte';

  type Color = {
    id: number;
    name: string;
    hexcode: string;
  }

  let colors: Color[] = $state([])

  // lifecycle method to call when the component is mounted
  onMount(() => {
    console.log('App component mounted')

    fetch(`${import.meta.env.VITE_API_URL}/colors`, {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer a1sd422s5f3s212gfc3s',
        'Organization': '1D5GHT',
      },
    })

      .then(response => response.json())
      .then(colorsData => colors = colorsData)
  })
  
</script>

<main>
  <h1>Color Tool</h1>

  <ul>
    {#each colors as color}
      <li>{color.name} - {color.hexcode}</li>
    {/each}
  </ul>
</main>

<style>
</style>
