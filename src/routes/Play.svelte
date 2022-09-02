<script lang="ts">
	export let playing = false;
	export let bpm = 120;
</script>

<div class="flex items-center space-x-4">
	<button on:click={() => (playing = !playing)} class="flex h-10 w-40 items-center justify-center rounded-full bg-gradient-to-br from-purple-500 to-pink-500 text-white transition duration-200 hover:from-purple-700 hover:to-pink-700">
		{#if playing}
			<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="mr-2 h-5 w-5">
				<path d="M5.25 3A2.25 2.25 0 003 5.25v9.5A2.25 2.25 0 005.25 17h9.5A2.25 2.25 0 0017 14.75v-9.5A2.25 2.25 0 0014.75 3h-9.5z" />
			</svg>
			Stop
		{:else}
			<svg viewBox="0 0 20 20" fill="currentColor" class="mr-2 h-5 w-5">
				<path d="M6.3 2.841A1.5 1.5 0 004 4.11V15.89a1.5 1.5 0 002.3 1.269l9.344-5.89a1.5 1.5 0 000-2.538L6.3 2.84z" />
			</svg>
			Play
		{/if}
	</button>
	<div class="w-28">BPM:{bpm}</div>
	<input min="50" max="160" type="range" bind:value={bpm} class="h-1 w-full cursor-pointer appearance-none rounded-full bg-gray-400" />
</div>
