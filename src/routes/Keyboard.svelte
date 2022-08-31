<script lang="ts">
  import { each } from "svelte/internal";

  export let octaves = 3;
  const natural: boolean[] = [
    true,
    false,
    true,
    false,
    true,
    true,
    false,
    true,
    false,
    true,
    false,
    true,
  ];
  console.log(natural[0]);
</script>

<div class="flex justify-center my-8">
  {#each Array(octaves) as _, octave}
    {#each Array(12) as _, nota}
      {#if natural[nota]}
        <button
          class="drop-shadow-lg h-28 w-8 bg-white rounded-md hover:bg-gray-200"
        />
      {:else}<button
          class="h-16 w-6 -mx-3 z-10 bg-black rounded-b-full hover:bg-gray-600"
        />{/if}
    {/each}
  {/each}
</div>
