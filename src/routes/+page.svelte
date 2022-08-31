<script lang="ts">
  import Keyboard from "./keyboard.svelte";

  let nota: string = "";
</script>

<div class="bg-slate-100 min-h-screen">
  <h1 class="text-3xl font-bold underline flex justify-center p-6">
    Nota: {nota}
  </h1>
  <Keyboard />
</div>
