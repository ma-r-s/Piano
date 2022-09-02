<script>
	export let selectedChords = [
		{ note: "C", quality: "M7" },
		{ note: "D", quality: "m7" },
		{ note: "E", quality: "m7" },
		{ note: "F", quality: "M7" },
	];
	export let maxChords = 12;
	const notes = ["C", "C#", "D", "D#", "E", "F", "F#", "G", "G#", "A", "A#", "B"];
	const qualities = ["M", "m", "dim", "M7", "m7", "sus2", "sus4", "dim7", "m9", "M9"];
	//Add random chord if there are less than maxChords chords
	const addChord = () => {
		if (selectedChords.length < maxChords) {
			selectedChords = [
				...selectedChords,
				{
					note: notes[Math.floor(Math.random() * notes.length)],
					quality: qualities[Math.floor(Math.random() * qualities.length)],
				},
			];
		}
	};
	//Remove last chord if there is at least one chord
	const removeChord = () => {
		if (selectedChords.length > 1) {
			selectedChords = selectedChords.slice(0, -1);
		}
	};
</script>

<div class="flex max-w-xl flex-wrap justify-center">
	{#each selectedChords as _, chord}
		<button class="m-3 flex flex-col rounded-lg bg-white p-1 shadow-lg transition duration-300 ease-out hover:-translate-y-1 hover:scale-110">
			<select class="m-2 bg-transparent text-center font-semibold " bind:value={selectedChords[chord].note}>
				{#each notes as note}
					<option value={note}>{note}</option>
				{/each}
			</select>
			<select class="m-2 bg-transparent text-center text-sm text-gray-500" bind:value={selectedChords[chord].quality}>
				{#each qualities as quality}
					<option value={quality}>{quality}</option>
				{/each}
			</select>
		</button>
	{/each}
	<div class="m-2 flex flex-col justify-evenly">
		{#if selectedChords.length < maxChords}
			<button on:click={addChord} class="m-1 flex h-8 w-12 items-center justify-center rounded-full bg-sky-500 p-2.5 text-3xl font-bold  text-white shadow-lg transition duration-200 hover:bg-sky-600">
				<svg viewBox="0 0 20 20" fill="currentColor">
					<path d="M10.75 4.75a.75.75 0 00-1.5 0v4.5h-4.5a.75.75 0 000 1.5h4.5v4.5a.75.75 0 001.5 0v-4.5h4.5a.75.75 0 000-1.5h-4.5v-4.5z" />
				</svg>
			</button>
		{/if}
		{#if selectedChords.length > 1}
			<button on:click={removeChord} class="m-1 flex h-8 w-12 items-center justify-center rounded-full bg-sky-500 p-1.5 text-3xl font-bold  text-white shadow-lg transition duration-200 hover:bg-sky-600">
				<svg viewBox="0 0 20 20" fill="currentColor">
					<path d="M6.75 9.25a.75.75 0 000 1.5h6.5a.75.75 0 000-1.5h-6.5z" />
				</svg>
			</button>
		{/if}
	</div>
</div>
