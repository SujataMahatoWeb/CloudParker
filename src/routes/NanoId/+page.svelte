<script lang="ts">
	import Navbar from "$lib/navbar/navbar.svelte";
  // import { onMount } from "svelte";
  
  let includeNumbers = true;
  let includeUpper = true;
  let includeLower = true;
  let includeSymbols = true;
  let excludeSimilar = false;

  let seeds = "2346789abcdefghijkmnpqrtwxyzABCDEFGHJKLMNPQRTUVWXYZ_-";

  let length = 5;
  let count = 10;
  let generated = [];

  const similarChars = "1lI0OouvsS";

  function generateNanoIDs() {
    let charset = "";

    if (includeNumbers) charset += "0123456789";
    if (includeUpper) charset += "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    if (includeLower) charset += "abcdefghijklmnopqrstuvwxyz";
    if (includeSymbols) charset += "_-";

    if (excludeSimilar) {
      charset = charset
        .split("")
        .filter((c) => !similarChars.includes(c))
        .join("");
    }

    if (!charset.length) {
      alert("Please select at least one character set."); 
      return;
    }

    generated = Array.from({ length: count }, () => randomID(charset));
  }

  function randomID(charset) {
    let id = "";
    for (let i = 0; i < length; i++) {
      const randomIdx = Math.floor(Math.random() * charset.length);
      id += charset[randomIdx];
    }
    return id;
  }

  function clearIDs() {
    generated = [];
  }

  let viewMode = "table";

  function copyToClipboard(text) {
    navigator.clipboard.writeText(text);
    alert("Copied: " + text);
  }
</script>

<Navbar />

<div class="max-w-3xl mx-auto p-6">
  <h1 class="text-4xl lg:text-6xl my-6 lg:my-10 font-bold text-center text-red-600">Nano ID Generator</h1>
</div>
  <!-- Config Section -->
<div class="max-w-6xl mx-auto mt-10 p-6 bg-white rounded-2xl shadow-2xl shadow-purple-200">
  <div class="p-4 ">
    <h2 class="text-xl font-bold py-3 text-black/60">Nano-ID Config</h2>

    <div class="grid grid-cols-1 lg:grid-cols-2 gap-3">
      <label class="flex items-center font-semibold gap-2">
        <input type="checkbox" bind:checked={includeNumbers} 
          class="w-5 h-5 
                  border-2 border-gray-300 rounded
                  bg-white

                  appearance-none
                  outline-none

                  focus:border-red-600
                  active:border-red-600

                  focus:outline-none
                  focus:ring-2
                  focus:ring-red-500
                  ring-offset-2

                  checked:bg-red-600
                  checked:border-red-600"
        /> 
        Include Numbers
      </label>

      <label class="flex items-center font-semibold gap-2">
        <input type="checkbox" bind:checked={includeLower} 
        class="w-5 h-5 
                  border-2 border-gray-300 rounded
                  bg-white

                  appearance-none
                  outline-none

                  focus:border-red-600
                  active:border-red-600

                  focus:outline-none
                  focus:ring-2
                  focus:ring-red-500
                  ring-offset-2

                  checked:bg-red-600
                  checked:border-red-600"
        /> 
         Lowercase Letters
      </label>

      <label class="flex items-center font-semibold gap-2">
        <input type="checkbox" bind:checked={excludeSimilar}
        class="w-5 h-5 
                  border-2 border-gray-300 rounded
                  bg-white

                  appearance-none
                  outline-none

                  focus:border-red-600
                  active:border-red-600

                  focus:outline-none
                  focus:ring-2
                  focus:ring-red-500
                  ring-offset-2

                  checked:bg-red-600
                  checked:border-red-600"
        />
        Exclude Similar Characters (1 l I 0 O o u v S s)
      </label>

      <label class="flex items-center font-semibold gap-2">
        <input type="checkbox" bind:checked={includeUpper}
        class="w-5 h-5 
                  border-2 border-gray-300 rounded
                  bg-white

                  appearance-none
                  outline-none

                  focus:border-red-600
                  active:border-red-600

                  focus:outline-none
                  focus:ring-2
                  focus:ring-red-500
                  ring-offset-2

                  checked:bg-red-600
                  checked:border-red-600"
        /> 
        Include Uppercase Letters
      </label>

      <label class="flex items-center gap-2 cursor-pointer font-semibold">
        <input
            type="checkbox"
            bind:checked={includeSymbols}
            class="w-5 h-5 
                  border-2 border-gray-300 rounded
                  bg-white

                  appearance-none
                  outline-none

                  focus:border-red-600
                  active:border-red-600

                  focus:outline-none
                  focus:ring-2
                  focus:ring-red-500
                  ring-offset-2

                  checked:bg-red-600
                  checked:border-red-600"
          />
            Include Symbols ( _ - )
      </label>
    </div>
  </div>

  <!-- Seeds -->
  <div class="p-4 ">
    <label class="font-bold text-black/60">Seeds</label>
    <input class="w-full border border-gray-200 focus:outline-0 ring-0 bg-gray-100 rounded p-2 mt-1" bind:value={seeds} />
  </div>

  <!-- Length and Count -->
  <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
    <div class="p-4 ">
      <label class="font-bold text-black/60">ID Length</label>
      <input type="number" class="w-full border border-gray-200 bg-gray-100 rounded p-2 mt-1" bind:value={length} />
    </div>

    <div class="p-4">
      <label class="font-bold text-black/60">How many nano id required ?</label>
      <input type="number" class="w-full border border-gray-200 bg-gray-100 rounded p-2 mt-1" bind:value={count} />
    </div>
  </div>

  <!-- Buttons -->
  <div class="flex gap-4 p-4 ">
    <button class="bg-red-600 text-white px-4 py-2 rounded" on:click={generateNanoIDs}>GENERATE</button>
    <button class="bg-gray-200 text-black px-4 py-2 rounded" on:click={clearIDs}>CLEAR</button>
  </div>

  <!-- Generated Table -->
  {#if generated.length}
    <div class="p-4">
      <h2 class="text-xl font-bold text-black/60 mb-3">Generated Nano-IDs</h2>

      <div class="my-3 flex flex-wrap gap-3">
    <button 
    class="py-2 px-4 rounded"
    class:bg-red-600={viewMode === "table"}
    class:text-white={viewMode === "table"}
    class:bg-gray-200={viewMode !== "table"}
    on:click={() => viewMode = "table"}>
    Table
  </button>

  <button 
    class="py-2 px-4 rounded"   
    class:bg-red-600={viewMode === "line"}
    class:text-white={viewMode === "line"}
    class:bg-gray-200={viewMode !== "line"}
    on:click={() => viewMode = "line"}>
    Line
  </button>

  <button 
    class="py-2 px-4 rounded"
    class:bg-red-600={viewMode === "comma"}
    class:text-white={viewMode === "comma"}
    class:bg-gray-200={viewMode !== "comma"}
    on:click={() => viewMode = "comma"}>
    Comma
  </button>
      </div> 

      {#if viewMode === "table"}
      <table class="w-full border">
        <thead>
          <tr class="border bg-gray-100">
            <th class="p-2">Index</th>
            <th class="p-2">Nano-ID</th>
            <th class="p-2">Actions</th>
          </tr>
        </thead>

        <tbody>
          {#each generated as id, i}
            <tr class="border">
              <td class="p-2 text-center">{i + 1}</td>
              <td class="p-2 font-mono text-center">{id}</td>
              <td class="p-2">
                <div class="flex justify-center items-center">
                  <button
                    on:click={() => copyToClipboard(id)}
                    class="p-2 rounded cursor-pointer transition"
                    title="Copy">

                    <svg 
                      class="w-5 h-5" 
                      fill="currentColor" 
                      viewBox="0 0 24 24">

                      <path d="M19 21H8V7h11v14m0-16H8a2 2 0 0 0-2 2v14a2 
                      2 0 0 0 2 2h11a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2m-3-4H4a2 
                      2 0 0 0-2 2v14h2V3h12V1Z" />
                    </svg>

                  </button>
                </div>
              </td>

            </tr>
          {/each}
        </tbody>
      </table>
      {/if}

      {#if viewMode === "line"}
        <div class="bg-gray-100 p-4 rounded font-mono space-y-2">
          {#each generated as id}
            <div>{id}</div>
          {/each}
        </div>
      {/if}

      {#if viewMode === "comma"}
        <div class="bg-gray-100 p-4 rounded font-mono break-all">
          {generated.join(", ")}
        </div>
      {/if}

    </div>
  {/if}

</div>

<style>
  body {
    background: #f5f7fa;
  }
</style>





