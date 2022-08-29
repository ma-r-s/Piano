<script lang="ts">
  let nota: string = "";
  const notasBlancas = [
    "C1",
    "D1",
    "E1",
    "F1",
    "G1",
    "A1",
    "B1",
    "C2",
    "D2",
    "E2",
    "F2",
    "G2",
    "A2",
    "B2",
  ];
</script>

<div class="bg-slate-100 min-h-screen">
  <h1 class="text-3xl font-bold underline flex justify-center p-6">
    Nota: {nota}
  </h1>
  <div class="flex justify-center my-8">
    <div class="absolute flex space-x-1">
      {#each notasBlancas as notaB}
        <button
          on:click={() => {
            nota = notaB;
          }}
          class="drop-shadow-lg h-28 w-8 bg-white rounded-md hover:bg-gray-200"
        />
      {/each}
    </div>
    <div class="absolute flex space-x-3">
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <div class="h-16 w-6" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <div class="h-16 w-6" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <div class="h-16 w-6" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
      <button class="h-16 w-6 bg-black rounded-b-full hover:bg-gray-600" />
    </div>
  </div>
</div>
