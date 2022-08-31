<script lang="ts">
  let nota = "";
  let notasBlancas: string[] = ["C", "D", "E", "F", "G", "A", "B"];
</script>

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
