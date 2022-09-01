<script lang="ts">
    import Keyboard from "./Keyboard.svelte";
    let nota: string = "";
    const handleMessage = (event: any) => {
        nota = event.detail;
    };
</script>

<div class="flex min-h-screen flex-col items-center bg-slate-100">
    <h1 class=" p-6 text-3xl font-bold underline">Nota: {nota}</h1>
    <Keyboard octaves={2} on:notePressed={handleMessage} />
</div>
