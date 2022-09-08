<script lang="ts">
	import { browser } from "$app/environment";
	import * as Tone from "tone";
	import Keyboard from "./Keyboard.svelte";
	import Selector from "./Selector.svelte";
	import Play from "./Play.svelte";
	import { Frequency } from "tone";
	let lastNote: number;
	let selected: number[] = [];
	let octaves = 2;
	let playing = false;
	let synth: Tone.PolySynth;
	let selectedChords = [
		{ note: "F", quality: "M7" },
		{ note: "D", quality: "m7" },
		{ note: "E", quality: "m7" },
		{ note: "F", quality: "M7" },
	];
	let qualities: { [key: string]: number[] } = {
		M: [0, 4, 7],
		m: [0, 3, 7],
		dim: [0, 3, 6],
		M7: [0, 4, 7, 11],
		m7: [0, 3, 7, 10],
		sus2: [0, 2, 7],
		sus4: [0, 5, 7],
		M9: [0, 4, 7, 10, 14],
		m9: [0, 3, 7, 10, 14],
	};

	let selectedNotes: any;
	$: selectedNotes = selectedChords.map((chord) => {
		return Tone.Frequency(chord.note + "3").harmonize(qualities[chord.quality]);
	});

	if (browser) {
		synth = new Tone.PolySynth().toDestination();
	}

	const notePressed = (note: CustomEvent) => {
		lastNote = note.detail;
		synth.triggerAttackRelease(Tone.Frequency("C3").transpose(note.detail).toFrequency(), "8n");
	};

	const chordPressed = (chord: CustomEvent) => {
		synth.triggerAttackRelease(selectedNotes[chord.detail], "8n");
	};
</script>

<div class="flex min-h-screen flex-col items-center space-y-4 bg-slate-100">
	<h1 class="p-4 text-3xl font-bold underline">Nota: {lastNote}</h1>
	<Keyboard on:notePressed={notePressed} bind:selected bind:octaves />
	<Play bind:playing />
	<Selector on:chordPressed={chordPressed} maxChords={8} bind:selectedChords />
</div>
