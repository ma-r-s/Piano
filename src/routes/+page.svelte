<script lang="ts">
    import Keyboard from "./Keyboard.svelte";
    let nota: string = "";
    const handleMessage = (event: any) => {
        nota = event.detail;
    };
</script>

<div class="min-h-screen bg-slate-100">
    <h1 class="flex justify-center p-6 text-3xl font-bold underline">Nota: {nota}</h1>
    <Keyboard octaves={2} on:notePressed={handleMessage} />
</div>
