<script lang="ts">
	import { createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher();
	export let octaves = 2;
	export let selected: number[] = [];
	const natural: boolean[] = [true, false, true, false, true, true, false, true, false, true, false, true];
</script>

<div class="flex">
	{#each Array(octaves * 12 + 1) as _, note}
		{#if natural[note % 12]}
			<button on:click={() => dispatch("notePressed", note)} class="mx-0.5 h-28 w-8 rounded-md transition duration-300 {selected.includes(note) ? 'bg-sky-500' : 'bg-white'} drop-shadow-lg {selected.includes(note) ? 'hover:bg-sky-400' : 'hover:bg-gray-200'}" />
		{:else}
			<button on:click={() => dispatch("notePressed", note)} class="z-10 -mx-3 h-16 w-6 rounded-b-full transition duration-300 {selected.includes(note) ? 'bg-sky-500' : 'bg-black'} {selected.includes(note) ? 'hover:bg-sky-400' : 'hover:bg-stone-700'}" />
		{/if}
	{/each}
</div>
