<script lang="ts">
	import Keyboard from "./Keyboard.svelte";
	import Selector from "./Selector.svelte";
	import Play from "./Play.svelte";
	let lastNote: number;
	let selected: number[] = [];
	let octaves = 2;
	let playing = false;
	let selectedChords = [
		{ note: "F", quality: "M7" },
		{ note: "D", quality: "m7" },
		{ note: "E", quality: "m7" },
		{ note: "F", quality: "M7" },
	];
	const notePressed = (note: CustomEvent) => {
		lastNote = note.detail;
		if (selected.includes(note.detail)) {
			selected = selected.filter((n) => n !== note.detail);
		} else {
			selected = [...selected, note.detail];
		}
	};
</script>

<div class="flex min-h-screen flex-col items-center space-y-4 bg-slate-100">
	<h1 class="p-4 text-3xl font-bold underline">Nota: {lastNote}</h1>
	<Keyboard on:notePressed={notePressed} bind:selected bind:octaves />
	<Play bind:playing />
	<Selector bind:selectedChords />
</div>
